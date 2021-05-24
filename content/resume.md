## Experience

### GetYourGuide AG

Relevant technologies:

**Languages:** Go, Python, Lua, Ruby<sup>1</sup>.

**Containers:** Kubernetes, Containerd, ECR, Docker<sup>1</sup>.

**Databases:** Aurora (MySQL), Kafka, Elastic Search, Simple Queue Service (SQS), S3, Percona XtraDB Cluster<sup>1</sup>, RabbitMQ<sup>1</sup>.

**Network:** Istio, Envoy, XDS, CloudFront (CDN), Route53, Calico, CoreDNS, Nginx<sup>1</sup>, HAProxy<sup>1</sup>.

**Security:** Open Policy Agent (OPA), GitHub Security Alerts, Dependabot.

**CI/CD:** Drone, Spinnaker, Github Actions, Helm, Kustomize.

**Observability:** DataDog (APM, Statsd, Network), Logging (FluentBit, Kafka, Elastic Search, Kibana).

**Infrastructure as Code:** CloudFormation, Terraform

**Configuration as Code:** Chef<sup>1</sup>.

**Workflow Management:** Apache Airflow.

> <sup>1</sup> Phased out technologies which played a big role at some point.

#### Senior Site Reliability Engineer - 2018/12 - Current

The DevOps team was formed by 6 people when I started at GetYourGuide, with contributions in hiring and onboarding team members, I helped to grow the team to 16 people and we split into specialized teams: Developer Enablement, Data Infrastructure, Security, and Reliability. As we were a single team taking care of the whole infrastructure at the beginning, I had contributions on different areas such as development tooling, CI/CD, computing, networking, databases, etc.

When I joined, the team had promoted the self-hosted Kubernetes cluster (based on Terraform and a set of Lambda functions) to production-ready and had the first microservice running in a dry-run mode. Since then, we have: containerized the monolith, moving it to Kubernetes, and supporting the new era of microservices at GetYourGuide. Today, all services run as containerized applications on top of Kubernetes.

In the infrastructure group, we have product areas in which I'm the co-owner of Compute and Network. Identifying customer (developers) problems and defining a roadmap to help improve their experience are in my pool of responsibilities within the team.

Some of the projects I was involved in:

-   Containerizing the monolith and adapting it for running in Kubernetes. This was a collaboration between various teams across engineering and required changes in different areas: application code, development tooling, CI/CD, and the infrastructure which was highly customized over the years to get the best in performance and high availability. My team was leading the project and some of my contributions were: identify blockers for parts of the system, implementing critical component changes as Memcached replication during the rollout and networking while running the two infrastructure platforms, hold other teams accountable during the project, coordinate the traffic shift during the migration while monitoring and identifying possible issues, etc.
-   Subject matter expert for Kubernetes, Istio, and Networking topics. Provide support and input in the different channels in the engineering organization as guilds, design reviews, regular support questions from development teams, and Post Mortems.
-   Modernized our custom Ingress and Firewall layer from Chef + Nginx + Lua to Kubernetes + Istio + Go sidecar. This enabled developers to define and own the routing to their services as a self-service. I led the project by holding design sessions, implementing code on critical parts of the systems while reviewing and defining tasks for other team members.
-   Go guild co-lead. Facilitate meetings and help teams using Go to do it most effectively by sharing common practices.
-   Led a small project to implement an Istio VirtualService testing framework to empower developers to roll out routing changes with confidence and reduce the risk of introducing regressions.
-   Created a custom autoscaler kubernetes operator for Airflow to gracefully scale up and down the number of workers running based on the number of tasks in the queue.
-   Defined an SRE checklist with requirements and guidelines for services before going to production according to its SLAs.
-   Infrastructure automation through kubernetes controllers and Lambda Functions.
-   Modernize our Kubernetes setup to use EKS, a big project to streamline how we run clusters by fully automating cluster management through controllers and pipelines that roll out changes in a uniform way across dozens of clusters.
-   Collaborated with a cross-functional team to introduce canary deployments to help to reduce the number of incidents caused by code changes.
-   Implemented an Envoy external authorization service that integrates with our internal OIDC broker to provide authentication and authorization capabilities for services in a generic way.
-   Knowledge sharing sessions within the team and the engineering group with topics as high available services in Kubernetes, leveraging istio capabilities, in-depth kubernetes, among others.

### Inova Tecnologias

#### Engineering Manager - 2013/04 – 2017/12

Relevant Technologies:

**Languages:** Python, Perl, TypeScript.

**Cloud Providers:** Amazon AWS, Azure.

**Databases:** MySQL, MariaDB, S3, Memcached, Redis.

**Obeservability:** Nagios, Zabbix, Cacti.

**Infrastructure as Code:** Terraform

**Configuration as Code:** Puppet

**Containers:** Docker

Fortunately, I had the opportunity to work alongside with great team members and we did awesome stuff together. Responsible for Devops and Engineering Team I’ve accumulated functions since I had never let the technical side.

Look for new business and partnership opportunities, getting better contracts, maintain ~400k hosting users and dozens of dedicated clusters, understand company and customer problems to create appropriate roadmaps, prioritize tickets based on pain points of the support team, manage government projects and do some code it’s just a few of my duties. Below some of things we’ve accomplished

-   Coordinate datacenter migration moving 200TB and 150 production vms within 128 public IPs, 3k domains(only 80% managed by us) with less than 4 hours and 1 minor issue felt by the users.
-   We’ve worked alongside Zimbra to help them fix several performance bugs impacting customers
-   Increase the customer satisfaction from 70% on avg. to 90%-98% over technical operations
-   Increased service availability from 95% in 2013 to 99.98-100% during 2014 and 2015
-   Migrated 100k users from dedicated and big customers to AWS avoiding datacenter infrastructure investments in 2014 and 2015
-   Established AWS technology partnership and ingressed in the fast track program getting marketing, poc and training funding.
-   Established AWS consulting partnership starting a new business for the company offering AWS managed services for customers
-   Earned the AWS Innovation Partner Award 2015 by helping customers migrate their data to AWS
-   Design, architecture and development of a new customer/reseller portal from ground up. This replaces the legacy portal with several ‘won’t fix bugs’ with new technologies and integrated with all services offered by the company
-   Fully automated config files, security updates with Puppet
-   Log archive project with Logstash, Elasticsearch, Kibana and Amazon S3 for government law requirements
-   Built Ops and Business KPIs using Datadog
-   Spread the culture of microservices and containers for the team
-   Delivered ~50 government projects with 100% satisfaction and mostly on-time since 2013 accumulating almost 1 MM migrated users from dozens of different platforms

#### System Administrator - 2010/10 – 2013/03

As IT Specialist I’ve led and executed the biggest success cases of the company. For my commitment within every project I got the opportunity to become Manager later I’ve accumulating a whole set of different skills. Virtualization and storage technologies, performance driven best practices, monitoring, development and automation was things often seen during this period.

-   Migration of the Email Platform of OAB-SP – Lawyers Association of Brazil – SP.
-   100k users, total of 5TB of data
-   Team: PM – 1 Engineer: Me
-   Several automation process including distribution of ssh certificates based on LDAP policies across all the 150 vms. It was a nightmare before that
-   Migration of the Email Platform of University of Sao Paulo.
-   240k users between students, professors and employees, 12TB
-   Team: PM – 1 Engineer: Me
-   Extension of the project above
-   25 University departments migrated to the recently created Email cluster of the University of Sao Paulo in less than 3 months, a total of 25k users and 3TB
-   Team: PM – 2 Engineers: Me + 1
-   Migration from bare metal to a 100% virtualized environment on the SAAS Platform
-   I’ve developed a transparent migration solution for the university of sao paulo using nginx, php and postfix. Two different platforms can run in parallel during a long migration period without impacts for the users(that was cool)
-   Over than 60 projects delivered between private and government customers
-   Zimbra official certification training instructor.

### Fiscaltech

#### System Administrator – Fiscaltech 2008/10 – 2010/10

Deployed and maintained Linux services running in over ten offices. File server, proxies, email, webservers, vpn connections and ITSM was some of the services I implemented.

## Education

Mackenzie Presbyterian University – M.Eng Electrical and Computing – 2016-2018 (dropped out)

FATEC-SP – Advanced Diploma Security Information  2010-2011 (dropped out)

Paulista University – Advanced Diploma Computer System Networking  2007-2009
