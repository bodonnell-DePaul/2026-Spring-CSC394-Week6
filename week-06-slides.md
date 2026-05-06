---
marp: true
theme: default
paginate: true
style: |
  section {
    font-family: Calibri, Arial, sans-serif;
    color: #172033;
    background: #f7f9fc;
  }
  h1, h2 {
    color: #17324d;
    letter-spacing: 0;
  }
  h1 {
    font-size: 44px;
  }
  h2 {
    font-size: 34px;
  }
  h3 {
    color: #2b6f77;
  }
  table {
    font-size: 22px;
  }
  th {
    background: #17324d;
    color: #ffffff;
  }
  td {
    background: #ffffff;
  }
  blockquote {
    border-left: 8px solid #d96c4b;
    color: #17324d;
    background: #fff6f2;
    padding: 0.35em 0.8em;
  }
  .lead {
    background: #17324d;
    color: #ffffff;
  }
  .lead h1, .lead h2, .lead h3, .lead strong {
    color: #ffffff;
  }
  .accent {
    color: #d96c4b;
    font-weight: 700;
  }
  .small {
    font-size: 24px;
  }
---

<!-- _class: lead -->

# Week 6 - Cloud Deployment Fundamentals

### CSC 394: Software Projects

DePaul University

---

<!-- header: 'Week 6 - Cloud Deployment Fundamentals' -->
<!-- footer: 'CSC 394 - DePaul University' -->

# Today's Big Idea

Cloud deployment is more than putting code online.

It is choosing and operating the pieces that make a web application reachable, reliable, secure, and repeatable.

| Concern | What It Decides |
| --- | --- |
| Compute | Where the app runs |
| Data | Where state survives |
| Networking | How traffic flows |
| Automation | How we repeat it safely |

---

# Learning Goals

By the end of today, you should be able to explain:

1. What AWS, Azure, and GCP have in common
2. VMs, containers, PaaS, and serverless
3. Core data storage and networking choices
4. What Infrastructure as Code is for
5. How IaC deployments differ from code deployments
6. Where GitHub Actions fits

---

<!-- _class: lead -->

# Section 1

## Cloud Providers Have the Same Building Blocks

---

# The Big Three

AWS, Azure, and GCP use different names, dashboards, and defaults.

Underneath, they solve the same problems:

| Need | AWS | Azure | GCP |
| --- | --- | --- | --- |
| Virtual machines | EC2 | Virtual Machines | Compute Engine |
| Object storage | S3 | Blob Storage | Cloud Storage |
| Private network | VPC | Virtual Network | VPC |
| Functions | Lambda | Azure Functions | Cloud Functions |

Learn the pattern first. Learn provider names second.

---

# Common Cloud Vocabulary

| Concept | Why It Matters |
| --- | --- |
| Account / subscription / project | Ownership, billing, and access boundary |
| Region | Where the resources physically run |
| Availability zone | Failure isolation inside a region |
| IAM / RBAC | Who or what can do each action |
| Monitoring | Logs, metrics, alerts, and traces |

The cloud is not one magic place. It is a catalog of services connected by policy and networking.

---

# Different Strengths, Same Core

| Provider | Common Reputation |
| --- | --- |
| AWS | Broadest ecosystem, first mover, huge service catalog |
| Azure | Enterprise integration, Microsoft identity, Windows and .NET fit |
| GCP | Data, analytics, Kubernetes heritage, developer-friendly services |

> The provider choice matters, but the architecture concepts transfer.

---

<!-- _class: lead -->

# Section 2

## Ways to Run a Web Application

---

# The Compute Spectrum

| Model | Control | Operations Work | Typical Fit |
| --- | --- | --- | --- |
| VM | Highest | Highest | Legacy apps, custom servers |
| Container | High | Medium | Portable app packaging |
| PaaS | Medium | Low | Web apps and APIs |
| Serverless | Lowest | Lowest per unit | Event-driven workloads |

More control usually means more responsibility.

Less control usually means faster delivery.

---

# Virtual Machines

A VM is a full server-like machine in the cloud.

You manage:

- Operating system updates
- Runtime installation
- Security patches
- Scaling and recovery
- Application process management

Best when you need maximum control or have legacy constraints.

---

# Containers

A container packages an app and its runtime assumptions into an image.

Containers help teams get consistency across:

- Developer laptops
- CI runners
- Staging
- Production

Useful when reproducibility and portability matter more than platform simplicity.

---

# PaaS and Serverless

| Model | What It Means | Watch For |
| --- | --- | --- |
| PaaS | Deploy an app without managing most server details | Less low-level control |
| Serverless | Run code because an event happens | Cold starts, limits, distributed debugging |

PaaS usually handles runtime hosting, HTTPS, routing, logs, and basic scaling.

Serverless fits requests, schedules, queue messages, file uploads, and database events.

For most student web apps, PaaS plus a managed database is the easiest cloud shape.

---

<!-- _class: lead -->

# Section 3

## Data Storage and Networking

---

# Data Storage Choices

| Storage Type | Best For |
| --- | --- |
| Managed relational DB | Users, tasks, projects, permissions |
| Object storage | Images, files, exports, backups |
| Block storage | VM disks and specialized workloads |
| NoSQL database | Flexible documents or high-scale key lookups |
| Cache | Fast temporary data and repeated queries |

Applications are replaceable. Data is not.

---

# Data Questions Before Deploying

Ask these before choosing storage:

- Does the data need relationships and transactions?
- How durable does it need to be?
- How will backups and restores work?
- Should the data be public, private, or both?
- What happens if the app deploy fails during a data change?

Most TaskBoard-style apps should start with a managed relational database.

---

# Networking Basics

| Concept | Plain-English Meaning |
| --- | --- |
| DNS | Names point users to services |
| HTTPS | Traffic is encrypted |
| Load balancer | Sends traffic to healthy app instances |
| VPC / virtual network | Private cloud network boundary |
| Firewall / security group | Rules for allowed traffic |
| CDN | Static content cached near users |

The safest default: expose the app, protect the data.

---

# Common Web App Shape

User browser -> frontend -> API -> database

Public side:

- Domain name
- HTTPS endpoint
- Frontend and API routes

Private side:

- Database
- Internal service traffic
- Secrets and credentials

---

<!-- _class: lead -->

# Section 4

## Infrastructure as Code

---

# What Is IaC?

Infrastructure as Code describes cloud resources in versioned files or repeatable automation.

IaC can manage:

- App services, VMs, containers, and functions
- Databases, storage, queues, and caches
- Networks, firewalls, and load balancers
- IAM roles, policies, and deployment permissions
- Monitoring and alerting resources

Goal: make infrastructure reviewable, repeatable, and less dependent on dashboard memory.

---

# Why IaC Matters

| Without IaC | With IaC |
| --- | --- |
| Dashboard clicks are forgotten | Desired state is versioned |
| Staging drifts from production | Environments can match |
| Changes are hard to review | Pull requests show intent |
| Disaster recovery depends on memory | Resources can be recreated |

IaC turns infrastructure into part of the engineering process.

---

# Approach 1: Declarative IaC

Declarative tools describe the desired end state.

| Tool | Best Fit |
| --- | --- |
| Terraform | Multi-cloud and broad ecosystem workflows |
| CloudFormation | AWS-native infrastructure |
| Bicep | Azure-native infrastructure |

Good for long-lived resources: networks, databases, storage, app services, and permissions.

---

# Approach 2: SDKs and CLIs

Cloud-native SDKs and CLIs automate provider APIs directly.

Useful for:

- One-time operational tasks
- Short-lived review environments
- Credential rotation
- Resource lookups
- Custom workflow glue

Keep this automation small and repeatable. Hidden state inside scripts can be risky.

---

<!-- _class: lead -->

# Section 5

## IaC Deployments vs. Code Deployments

---

# Two Different Release Types

| Question | Code Deployment | IaC Deployment |
| --- | --- | --- |
| What changes? | App behavior | Cloud resources and config |
| Main artifact | App build or image | Resource definitions and state |
| Frequency | Often | More controlled |
| Risk | Bugs and downtime | Security, data, cost, downtime |
| Rollback | Run previous app version | Carefully restore desired state |

Infrastructure changes usually deserve slower gates.

---

# Managing Both Safely

| Code Deployment | IaC Deployment |
| --- | --- |
| Build once, promote the same artifact | Preview planned changes before applying |
| Run automated tests before release | Review security, cost, and data impact |
| Use staging before production | Require approvals for production |
| Keep releases traceable to commits | Protect state files and deployment credentials |
| Make rollback fast and boring | Avoid storing secrets in IaC definitions |

Code asks: which version should run? IaC asks: what should exist?

---

# When They Meet

Some releases need both:

| First | Then |
| --- | --- |
| Create a database | Deploy app that uses it |
| Add a queue | Deploy worker that reads it |
| Add an environment variable | Deploy code that expects it |
| Update permissions | Deploy service that needs them |

Do not let every app deploy casually rewrite infrastructure.

---

<!-- _class: lead -->

# Section 6

## GitHub Actions as the Coordinator

---

# Application Workflow

A typical app workflow:

1. Trigger on pull request or merge
2. Run checks and tests
3. Build a deployable artifact
4. Deploy to staging
5. Promote to production after approval

This workflow protects app behavior.

---

# IaC Workflow and Guardrails

A typical infrastructure workflow:

1. Trigger on infrastructure file changes
2. Validate definitions
3. Produce a plan or preview
4. Review the planned changes in the pull request
5. Apply after merge, with production approval gates

Use protected environments, required reviewers, separate secrets per environment, least-privilege cloud credentials, and OpenID Connect where possible.

Automation should make the safe path easier than the risky path.

---

# Final Takeaway

Cloud providers differ in names and tools, but the architecture patterns repeat.

For web applications, keep asking:

1. Where does the code run?
2. Where does the data live?
3. How does traffic flow?
4. How do we repeat and review changes?

That is the foundation of cloud deployment.
