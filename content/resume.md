---
type: resume
title: Fernando Cainelli
---

<div class="resume-contact">
  <div class="resume-contact-row">
    <span><i class="fa fa-globe"></i> <a href="https://cainelli.me">cainelli.me</a></span>
    <span><i class="fa fa-github"></i> <a href="https://github.com/cainelli">github.com/cainelli</a></span>
    <span><i class="fa fa-whatsapp"></i> <a href="https://wa.me/5511950460448">+55 11 95046 0448</a></span>
  </div>
  <div class="resume-contact-row">
    <span><i class="fa fa-map-marker"></i> São Paulo - Brazil</span>
    <span><i class="fa fa-linkedin"></i> <a href="https://www.linkedin.com/in/cainelli/">linkedin.com/in/cainelli</a></span>
    <span><i class="fa fa-envelope"></i> <a href="mailto:fernando@cainelli.me">fernando@cainelli.me</a></span>
  </div>
</div>

# Summary

Site Reliability Engineer with over 15 years of experience in infrastructure, software development, distributed systems, and platform engineering. Specialized in Kubernetes, service mesh, and networking at scale. Proven track record of leading infrastructure modernization projects, growing teams, and improving system reliability in high-traffic environments.

# Skills

**Languages:** Go, Python, TypeScript, Lua
**Containers & Orchestration:** Kubernetes, EKS, Containerd, ECR, Helm, Kustomize, Argo Rollouts
**Networking:** Istio, Envoy, gRPC, Cloudflare, CloudFront (CDN), Route53, Calico, eBPF, CoreDNS
**Databases & Messaging:** Aurora (MySQL), Kafka, Elasticsearch, SQS, S3, Memcached, Redis
**Security:** OIDC, Open Policy Agent (OPA), Dependabot, GitHub Security Alerts
**CI/CD:** GitHub Actions, Argo CD, Drone, Spinnaker
**Observability:** Datadog (APM, StatsD, Network), FluentBit, Kibana
**Infrastructure as Code:** Terraform, CloudFormation, CDK
**Cloud Providers:** Amazon AWS, Azure

# Experience

## GetYourGuide AG

### Staff Site Reliability Engineer — 2022 – Present

Owner of the Compute and Network product areas within the infrastructure group. Setting technical vision and driving cross-org initiatives for Kubernetes, service mesh, and networking at scale. Responsible for identifying developer pain points, defining roadmaps, mentoring engineers, and ensuring platform reliability.

Key contributions:

- **Service definition redesign (gygservice.yml v2):** Led the redesign of the service definition format. Built tooling including linting, auto-fix, auto-updates (dependabot-like), and JSON schema for documentation and IDE IntelliSense. Rolled out across the org without developer intervention or incidents.
- **KIAM replacement:** Existing solutions (IRSA, Pod Identity) did not meet internal requirements. Built an in-house IMDS-based solution with a CSI driver, EnvoyFilter, and mutating webhooks.
- **Envoy open-source contributions:** 7 merged PRs to envoyproxy/envoy: added tracing propagation for ext_proc gRPC streams ([#33665](https://github.com/envoyproxy/envoy/pull/33665), [#34395](https://github.com/envoyproxy/envoy/pull/34395)), fixed 504 timeout responses ([#34856](https://github.com/envoyproxy/envoy/pull/34856)), fixed 100% trace sampling bug ([#37794](https://github.com/envoyproxy/envoy/pull/37794)), plus test and docs fixes.
- **HPA resilience:** Implemented secondary scaling metric fallback preventing SEV-1 outages during Datadog incidents.
- **Multicluster strategy & failover:** Designed multi-account EKS architecture with multicluster networking, failover controllers, and automated workload toggling.
- **Cloudflare migration:** Migrated 45+ domains from CloudFront, saving $12k/month. Built replay testing tooling and a multi-stage weighted rollout with zero customer-facing incidents.
- **Rate limiting service:** Built a custom Envoy RLS in Go with <1ms latency. Survived Redis outages gracefully; 45+ developer policy changes in the first months.
- **External Processing migration:** Replaced Lua-based ingress integration with Envoy External Processor Filter, moving from HTTP callouts to gRPC. Completed migration in two weeks using a feature flag via custom resources for seamless transition.
- **Cluster test framework:** Built custom cluster integration tests that run on every cluster management layer change (EKS upgrades, addon updates) to prevent regressions in new versions.
- **Cost optimizations:** Cross-AZ traffic savings ~$30k/year, Confluent data volume reduction of 60–70%, CDN batching savings ~25%.
- **Hiring & interview process:** Championed and revamped the SRE interview process with a hands-on take-home task using the production stack, receiving consistently positive candidate feedback.

### Senior Site Reliability Engineer — Dec 2018 – 2022

Joined as part of a 6-person DevOps team. Contributed to hiring and onboarding to grow the team to 16 engineers, which later split into specialized teams: Developer Enablement, Data Infrastructure, Security, and Reliability. As the team evolved, I contributed across development tooling, CI/CD, compute, networking, and databases.

Key contributions:

- **EKS migration:** Led the modernization of the Kubernetes setup to EKS across ~300 services with zero downtime. Built a migration controller and automated cluster management through pipelines, rolling out changes uniformly across 20+ clusters.
- **Ingress modernization:** Led the redesign of the Ingress and Firewall layer from Chef + Nginx + Lua to Kubernetes + Istio + Go sidecar, enabling developers to self-service their routing configurations. Held design sessions, implemented critical components, and coordinated the team.
- **Envoy auth service:** Implemented an Envoy external authorization service integrated with an internal OIDC broker, providing transparent token refresh, auditing, and generic authentication and authorization capabilities across services.
- **Monolith containerization:** Led critical parts of the cross-team effort to containerize the monolith and migrate it to Kubernetes. Identified blockers, implemented Memcached cluster replication and network communication for the rollout, coordinated the traffic shift, and monitored the migration process.
- **Canary deployments:** Collaborated with a cross-functional team to introduce canary deployments, reducing the number of incidents caused by code changes.
- **VirtualService testing framework:** Led the implementation of an Istio VirtualService testing framework, enabling developers to validate routing changes before rollout and reducing regression risk.
- **Airflow autoscaler:** Built a custom Kubernetes operator to gracefully autoscale Airflow workers based on task queue depth.
- **Infrastructure automation:** Built Kubernetes controllers and Lambda functions to automate infrastructure operations.
- **Go guild co-lead:** Facilitated meetings and promoted best practices for Go across engineering teams.
- **Knowledge sharing:** Delivered sessions on high-availability in Kubernetes, Istio capabilities, and Kubernetes internals to the broader engineering organization.

## Inova Tecnologias

### Engineering Manager — Apr 2013 – Dec 2017

Managed the DevOps and Engineering team while remaining hands-on technically. Responsibilities included identifying new business and partnership opportunities, negotiating contracts, managing 400k+ hosting users across dozens of dedicated clusters, creating roadmaps based on company and customer needs, prioritizing work based on support team pain points, managing government projects, and writing code.

**Technologies:** Python, Perl, TypeScript, Amazon AWS, Azure, MySQL, MariaDB, Memcached, Redis, Nagios, Zabbix, Terraform, Puppet, Docker

- Coordinated a datacenter migration of 200TB, 150 production VMs, 128 public IPs, and 3k domains in under 4 hours.
- Improved customer satisfaction from 70% to 90–98% across technical operations.
- Increased service availability from 95% in 2013 to 99.98–100% during 2014 and 2015.
- Migrated 100k users from dedicated environments to AWS, avoiding upfront datacenter infrastructure investments.
- Established AWS Technology Partnership and joined the Fast Track program, securing marketing, POC, and training budget.
- Established AWS Consulting Partnership, creating a new product pillar offering AWS managed services.
- Earned the AWS Innovation Partner Award 2015 for helping customers migrate to AWS.
- Designed and developed a new customer/reseller portal from scratch, replacing the legacy portal and integrating all company services.
- Automated configuration management and security updates with Puppet.
- Built a log archival pipeline with Logstash, Elasticsearch, Kibana, and S3 for compliance requirements.
- Defined operational and business KPIs using Datadog.
- Delivered ~50 government projects with 100% satisfaction, accumulating nearly 1M migrated users from dozens of platforms.
- Collaborated with Zimbra to identify and fix performance bugs impacting customers.

### System Administrator — Oct 2010 – Mar 2013

Led and executed the company's largest migration projects, building expertise in virtualization, storage, performance optimization, monitoring, and automation.

- Migrated the email platform of OAB-SP (Lawyers Association of Brazil – SP): 100k users, 5TB of data.
- Migrated the email platform of the University of Sao Paulo: 240k users, 12TB of data.
- Migrated 25 university departments (25k users, 3TB) from diverse email platforms to a unified cluster in under 3 months.
- Developed a transparent migration solution using Nginx, PHP, and Postfix, allowing two platforms to run in parallel during long migrations without user impact.
- Automated SSH certificate distribution based on LDAP policies across 150 VMs, streamlining engineer onboarding and offboarding.
- Delivered over 60 projects across private and government customers.
- Served as a Zimbra official certification training instructor.
- Migrated the SaaS product from bare metal to a fully virtualized environment.

## Fiscaltech

### System Administrator — Oct 2008 – Oct 2010

Deployed and maintained Linux services across ten+ offices, including file servers, proxies, email, web servers, VPN, and ITSM.

# Education

Mackenzie Presbyterian University — Coursework in Electrical and Computing Engineering, 2016–2018

FATEC-SP — Coursework in Information Security, 2010–2011

Paulista University — Advanced Diploma in Computer System Networking, 2007–2009
