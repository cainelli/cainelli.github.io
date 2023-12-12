# Experience

## GetYourGuide AG

Relevant technologies:

**Languages:** Go, Python, Lua, Ruby¹ ; **Containers:** Kubernetes, Containerd, ECR, Docker¹ ; **Databases:** Aurora (MySQL), Kafka, Elastic Search, Simple Queue Service (SQS), S3, Percona XtraDB Cluster¹ , RabbitMQ¹ ; **Network:** Istio, Envoy, XDS, CloudFront (CDN), Route53, Calico, CoreDNS, Nginx¹ , HAProxy¹ ; **Security:** Open Policy Agent (OPA), GitHub Security Alerts, Dependabot; **CI/CD:** Drone, Spinnaker, Github Actions, Helm, Kustomize; **Cloud Providers:** Amazon AWS; **Observability:** DataDog (APM, Statsd, Network), Logging (FluentBit, Kafka, Elastic Search, Kibana); **Infrastructure as Code:** CloudFormation, Terraform; **Configuration as Code:** Chef¹ ; **Workflow Management:** Apache Airflow.

¹ Phased out technologies which played a big role at some point.

### Senior Site Reliability Engineer - 2018/12 - Current

The DevOps team was formed by 6 people when I started at GetYourGuide, with contributions in hiring and onboarding team members, I helped to grow the team to 16 people and we split into specialized teams: Developer Enablement, Data Infrastructure, Security, and Reliability. As we were a single team taking care of the whole infrastructure at the beginning, I had contributions on different areas such as development tooling, CI/CD, computing, networking, databases, etc.

When I joined, the team had promoted the self-hosted Kubernetes cluster to production-ready and had the first microservice running in a dry-run mode. Together we containerized the monolith, had all services running on Kubernetes, improved the existing and added new capabilities to the platform empowering developers with self-services, and support them to improve the overall availability and resilience of our systems in the new distributed architecture while enabling them to be more efficient delivering features to the customers.

In the infrastructure group, we have product areas in which I'm the co-owner of Compute and Network. Identifying customer (developers) problems and defining a roadmap to help improve their experience are in my pool of responsibilities within the team.

Some of the projects I was involved in:

- Containerizing the monolith and adapting it for running on Kubernetes. This was a collaboration between various teams across engineering and required changes in different areas: application code, development tooling, CI/CD, and infrastructure. My team was leading the project and some of my contributions were: identify blockers and propose solutions for parts of the project I owned, implementing critical changes as Memcached cluster replication and network communication during the rollout, coordinate the traffic shift, and monitoring the overall service move process.
- Subject matter expert for Kubernetes, Istio, and Networking topics. Provide support and input in the different channels in the engineering organization as guilds, design reviews, regular support questions from development teams, and Post Mortems.
- Modernized our custom Ingress and Firewall layer from Chef + Nginx + Lua to Kubernetes + Istio + Go sidecar. This enabled developers to define and own the routing to their services as a self-service. I led the project by holding design sessions, implementing code on critical parts of the systems while reviewing and defining tasks for other team members.
- Go guild co-lead. Facilitate meetings and help teams using Go to do it most effectively by sharing common practices.
- Led a small project to implement an Istio VirtualService testing framework to empower developers to roll out routing changes with confidence and reduce the risk of introducing regressions.
- Created a custom autoscaler kubernetes operator for Airflow to gracefully scale up and down the number of workers running based on the number of tasks in the queue.
- Defined an SRE checklist with requirements and guidelines for services before going to production according to its SLAs.
- Infrastructure automation through kubernetes controllers and Lambda Functions.
- Modernize our Kubernetes setup to use EKS, a big project to streamline how we run clusters by fully automating cluster management through controllers and pipelines that roll out changes in a uniform way across dozens of clusters.
- Collaborated with a cross-functional team to introduce canary deployments to help to reduce the number of incidents caused by code changes.
- Implemented an Envoy external authorization service that integrates with our internal OIDC broker to provide authentication and authorization capabilities for services in a generic way.
- Knowledge sharing sessions within the team and the engineering group with topics as high available services in Kubernetes, leveraging istio capabilities, in-depth kubernetes, among others.

### Inova Tecnologias

Relevant Technologies:

**Languages:** Python, Perl, TypeScript; **Cloud Providers:** Amazon AWS, Azure; **Databases:** MySQL; MariaDB, S3, Memcached, Redis; **Observability:** Nagios, Zabbix, Cacti; **Infrastructure as Code:** Terraform; **Configuration as Code:** Puppet; **Containers:** Docker

#### Engineering Manager - 2013/04 – 2017/12

I had the opportunity to work alongside great team members and we did awesome stuff together. Responsible for DevOps and Engineering Team I’ve accumulated functions since I had never let the technical side.

Look for new business and partnership opportunities, getting better contracts, maintain over 400k hosting users and dozens of dedicated clusters, understand company and customer problems to create appropriate roadmaps, prioritize tickets based on pain points of the support team, manage government projects and do some code was just a few of my duties. Below some of the things we’ve accomplished

- Coordinate datacenter migration moving 200TB and 150 production vms with 128 public IPs, 3k domains(only 80% managed by us) in less than 4 hours.
- We’ve worked alongside Zimbra to help them fix several performance bugs impacting customers
- Increase the customer satisfaction from 70% on avg. to 90%-98% over technical operations
- Increased service availability from 95% in 2013 to 99.98-100% during 2014 and 2015
- Migrated 100k users from dedicated environments and big customers to AWS avoiding data center infrastructure upfront investments in 2014 and 2015
- Established AWS technology partnership and ingressed in the fast track program getting marketing, POC, and training budget from AWS.
- Established AWS consulting partnership starting a new product pillar offering AWS managed services for customers
- Earned the AWS Innovation Partner Award 2015 by helping customers migrate their data to AWS
- Design, architecture, and development of a new customer/reseller portal from the ground up. It replaced the legacy portal with several ‘won’t fix bugs’ and integrated with all services offered by the company
- Fully automated config files, security updates with Puppet
- Log archive project with Logstash, Elasticsearch, Kibana, and Amazon S3 due to compliance laws.
- Defined operational and Business KPIs using Datadog
- Delivered ~50 government projects with 100% satisfaction and mostly on-time since 2013 accumulating almost 1 MM migrated users from dozens of different platforms

#### System Administrator - 2010/10 – 2013/03

I’ve led and executed the biggest success cases of the company. For my commitment to every project, I got the opportunity to become a Manager later I’ve accumulated a whole set of different skills. Virtualization and storage technologies, performance-driven best practices, monitoring, development, and automation were things often seen during this period.

- Migration of the email platform of OAB-SP – Lawyers Association of Brazil – SP: 100K users and 5TB of mail data.
- Automated many processes including distribution of SSH certificates based on LDAP policies in 150 virtual machines making easier onboarding and offboarding of engineers.
- Migration of the email platform of the University of Sao Paulo, 240K users and 12TB of main data.
- 25 University departments migrated to the cluster of the University of Sao Paulo in less than 3 months, a total of 25k users and 3TB and different email platform sources.
- Developed a transparent migration solution for the University of Sao Paulo using Nginx, PHP, and Postfix. Two different platforms could run in parallel during a long migration period without impacts for the users.
- Over 60 projects delivered between private and government customers.
- Zimbra official certification training instructor.
- Migration from bare metal to a 100% virtualized environment on the SAAS product.

### Fiscaltech

#### System Administrator – Fiscaltech 2008/10 – 2010/10

Deployed and maintained Linux services running in over ten offices. File server, proxies, email, webservers, vpn connections and ITSM was some of the services I implemented.

## Education

Mackenzie Presbyterian University – M.Eng Electrical and Computing – 2016-2018 (dropped out)

FATEC-SP – Advanced Diploma Security Information  2010-2011 (dropped out)

Paulista University – Advanced Diploma Computer System Networking  2007-2009
