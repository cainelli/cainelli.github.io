+++
date = "2020-10-30"
title = "Preventing traffic routing regressions for Istio Virtual Services"
slug = "preventing-traffic-routing-regressions-for-istio-virtual-services"
tags = []
categories = []
series = []
authors = ["Fernando Cainelli"]
+++


# Preventing traffic routing regressions for Istio Virtual Services

This article was originaly posted in [GetYourGuide's Inside Blog](https://inside.getyourguide.com/blog/2020/10/30/preventing-traffic-routing-regressions-for-istio-virtual-services).

## Understanding our traffic management

One of the Reliability team's responsibilities is to manage how traffic reaches our services, either from the internet, commonly known as north/south, or service to service, east/west.

We run all our services on Kubernetes, and we have been using Istio since the beginning of 2019 for both network use cases. This brings the benefit of having the same networking configuration for ingress and service to service traffic. All the external routing configurations live in a single repository with more than 60 VirtualServices.

A typical VirtualService configuration looks like:

{{< gist cainelli 984ab33f95a85a1a23a1ac57b5971012 "virtualservice.yml" >}}

The above VirtualService is bound to an Istio Ingress Gateway and the "mesh", a special keyword that assigns this configuration to all sidecar proxies in the cluster. The nice thing about it is that routing works seamlessly, independent of where the requests originate.

```
curl -XPOST https://awesome-api.getyourguide.com/customerResetPassword/ ...
```
                                    Request from Internet

```go
func main() {

	client := &http.Client{}

	req, err := http.NewRequest("POST", "http://awesome-api.awesome-api/customerResetPassword", nil)
	if err != nil {
		// handle err
	}

	req.Header.Add("Host", "awesome-api.getyourguide.com")
	resp, err := client.Do(req)
	if err != nil {
		// handle err
	}
}
```

                        Request from an internal service running in Kubernetes


You might have read about our [journey towards a distributed, service oriented architecture](https://inside.getyourguide.com/blog/2020/2/24/how-to-split-a-monolith-into-services). It's a long and gradual process: We're extracting business logic from the monolith piece by piece. Let's take a look at a hypothetical example of functionality being extracted and roughly the process behind it:

- The Travelers Platform team, responsible for core services in the monolith, wants to extract the user authentication functionality out of it as it’s too complex to maintain in the old stack.

- After a round of design sessions and feedback, the decision is to go with a trustful external identity provider to store users’ credentials.

- Existing helper functionalities in the monolith would be moved to a separate service such as custom reset passwords workflow or personal information clean up.

Once the team has implemented the reset password endpoints following the existing API contract, it then sets up a route in the [VirtualService](https://istio.io/latest/docs/concepts/traffic-management/#virtual-services):

{{< gist cainelli 4caeaf9f6594358c664e637946bd8288 "virtualservice.yml" >}}


From that moment, all reset password requests are being handled by the new service instead of the monolith transparently for internal and external clients.

## Some of the challenges with Istio

Having Istio in our toolbox helps teams split the monolith up, gain visibility, and improve the resilience of our services. However, in reality, it also brings complexity and other issues that need to be addressed. For the scope of this blog post we will limit the discussion to the following topics we have experienced:

- VirtualServices can be big and often contain advanced regular expressions. People are afraid to extend or optimize them.

- Engineers setting up the rules are not familiar with Istio configuration and regressions can easily be introduced.

- Time spent in pull request reviews is not linear with the number of changes in it. VirtualServices needs to be reviewed as a whole as rules might conflict with each other.

- Troubleshooting is hard. We need a deep understanding of Istio architecture and APIs, Envoy, HTTP Protocol, TCP, Kubernetes Networking, etc. When something goes wrong,  the MTTR (mean time to recovery) can take hours.

As our engineering teams move fast, the changes to VirtualServices are quite frequent, increasing the chances of bad configuration being deployed.

Let’s get back to our hypothetical scenario. Now, a different team is extracting the customers data to its dedicated service called `users`. When the service is ready to be deployed, the engineer working on this finds the `auth` service route and copy/paste it, changing the path and destination for it with the new `users` endpoints.


{{< gist cainelli 7a2b92a5f63049a2eded5333c8c16a06 "virtualservice.yml" >}}


The VirtualService looks legit until we read the whole file in detail. We can see that the route to `users` service is based on a `prefix` to `/customer`, and as the routes are evaluated top down, it also matches requests to `/customerResetPassword`. When this configuration is applied, password reset requests would go to the `users` service that doesn’t have this endpoint, returning a 404 error to the client. Such a mistake is easier to spot in a 30 liner file but is much harder in a 1000 lines one with complex rules in it.


## Introducing a validation tool

One way of minimizing the risks is to introduce safety nets; the earlier we spot the issues, the more confident we are rolling out changes. It's not new in software engineering to make use of unit tests to prevent regressions. Unfortunately, there's no such tool for Istio VirtualService configuration, so we decided to come up with a validator that:

1. could assert if your VirtualService change is doing what you want while you rest assured that existing routing behavior will not break.

2. run it locally and as part of CI (continuous integration) without the need for a Kubernetes + Istio setup.

3. have a simple test case API. They should be short to write but have extensive coverage.

The idea was pitched in a Hack Day* project. Two other engineers, Alexander Mack and Andreas Jaggi, who are passionate about testing, joined the project. After a couple of days of working, we came up with an [istio-config-validator](https://github.com/getyourguide/istio-config-validator). This tool reads all your local VirtualService configuration files and asserts against the test cases you create. Here is an example of how it works continuing with the VirtualService we have created:

We will start by writing our test cases for the routes we know of. That is typically what a developer will do before submitting a pull request:

{{< gist cainelli 2c7c81d18125450575b2932439c963ab "awesome-api-test.yml" >}}


Three test cases describing our intended behavior for routing were added. The full API specification for test cases is in the repository documentation, but let’s break down and understand what we’re defining here.

**description**: A short description of the test case. It is useful when a test case fails, and we want to identify which one.

**request**: It will be used as input for the VirtualService rule matching. A combination of all possible parameters such as authority, path, and headers will be used to mock requests.

**route**: What’s the exact destination expected? This is what will be used to assert against the result.

**wantMatch**: If you expect the assert to be true or false.

Let’s run istio-config-validator passing our test cases file and the directory where the VirtualServices are located.

```
$ istio-config-validator -t tests/ manifests/virtualservices/

running test: customers endpoints pointing to users service
PASS input:[{awesome-api.getyourguide.com GET /customers/1 map[]}]
PASS input:[{awesome-api.getyourguide.com GET /customers map[]}]
PASS input:[{awesome-api.getyourguide.com OPTIONS /customers/1 map[]}]
PASS input:[{awesome-api.getyourguide.com OPTIONS /customers map[]}]
PASS input:[{awesome-api.getyourguide.com PUT /customers/1 map[]}]
PASS input:[{awesome-api.getyourguide.com PUT /customers map[]}]
===========================
running test: authentication service endpoints
FAIL input:[{awesome-api.getyourguide.com GET /customerResetPassword map[]}]
2020-10-15T13:24:35.675470Z     fatal   destination mismatch=[destination:<host:"users.users.svc.cluster.local" > ], want [destination:<host:"auth.auth.svc.cluster.local" > ]
exit status 1
```

The validator failed on the authentication service endpoint test as a GET request to `https://awesome-api.getyourguide/customerResetPassword` went to the users service instead of the auth service. That’s enough information to fix the configuration.


{{< gist cainelli adab6831f62bef98fd52975b4fa04a09 "virtualservice.yml" >}}


There are different ways for solving it: here I chose to use regex matching over prefix. Running the command again, we see that all tests have now passed.

```
$ istio-config-validator -t tests/ manifests/virtualservices/

Test summary:
 - 3 testfiles, 3 configfiles
 - 3 testcases with 24 inputs passed
The validator mocks Istio's rule precedence logic for finding the right destination to assert. This is a naive approach, and we already received good feedback on how to improve it.
```

In general, we are quite happy with the outcome. Since we introduced it, developers have created more than 1,000 test inputs. They can run it locally, get immediate feedback, and deploy with confidence, putting us in a much better position than six months ago.

We have decided to open-source the project as we think others might be struggling with the same type of problems we were, and they can benefit from it. If you want to start using the validator or contribute, please [file an issue or PR in Github](https://github.com/getyourguide/istio-config-validator).

I want to thank Alexander Mack and Andreas Jaggi for their valuable contributions and for joining the project. It was pleasant to work with them while delivering something impactful for the Engineering teams.

*HackDays are 2-day hackathons where engineers are allowed to work on a project of their choice, with colleagues in varying domains across the organization. It provides an opportunity to try something new, build something impactful, and/or meet new people.
