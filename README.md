<!-- GitHub Profile README — atiladeoyetunji -->
<!-- To use: create a repo named exactly your GitHub username, add this as README.md -->

<div align="center">

# Oyetunji Atilade

### Senior DevOps & Cloud Infrastructure Engineer

*Building systems that scale, survive, and ship fast — from Africa to global.*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/oyetunji-atilade)
[![Email](https://img.shields.io/badge/Email-atiladeoyetunji@gmail.com-D14836?style=flat-square&logo=gmail)](mailto:atiladeoyetunji@gmail.com)

</div>

---

## What I Do

I architect and operate cloud infrastructure at scale. My work lives at the intersection of **DevOps**, **cloud-native engineering**, and **platform reliability** — building the foundations that let product teams ship without thinking about infrastructure.

Most of my production work is in private repos (company systems, client infrastructure). What you'll find here is the same quality of work, built to demonstrate the depth of that private experience.

**I think in systems.** Not just "does this work" but "does this survive a 3am pager alert, a black friday spike, and a junior engineer's first PR."

---

## Core Stack

<div align="left">

**Cloud & Infrastructure**
![AWS](https://img.shields.io/badge/AWS-Expert-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-Advanced-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-Advanced-326CE5?style=flat-square&logo=kubernetes&logoColor=white)

**Containers & CI/CD**
![Docker](https://img.shields.io/badge/Docker-Expert-2496ED?style=flat-square&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-Advanced-D24939?style=flat-square&logo=jenkins&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-Advanced-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**Observability**
![Prometheus](https://img.shields.io/badge/Prometheus-Advanced-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-Advanced-F46800?style=flat-square&logo=grafana&logoColor=white)
![Loki](https://img.shields.io/badge/Loki-Intermediate-F05032?style=flat-square&logo=grafana&logoColor=white)

**Databases & Messaging**
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Advanced-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-Advanced-DC382D?style=flat-square&logo=redis&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Intermediate-47A248?style=flat-square&logo=mongodb&logoColor=white)

**Languages & Scripting**
![Bash](https://img.shields.io/badge/Bash-Advanced-4EAA25?style=flat-square&logo=gnubash&logoColor=white)
![Python](https://img.shields.io/badge/Python-Intermediate-3776AB?style=flat-square&logo=python&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Advanced-339933?style=flat-square&logo=nodedotjs&logoColor=white)

</div>

---

## Featured Projects

These five repos form a connected system — the same architecture I build and operate for production workloads.

---

### 🏗️ [cultivo-aws-infrastructure-terraform](https://github.com/atiladeoyetunji/cultivo-aws-infrastructure-terraform)
> *Production AWS infrastructure — VPC, EKS, RDS, IAM — fully codified*

A complete, multi-environment AWS infrastructure built with Terraform modules. Not a tutorial clone — the same patterns I use to provision systems that run real workloads.

**What's inside:**
- VPC with public/private/isolated subnets across 3 AZs, NAT gateways, VPC Flow Logs
- EKS cluster with mixed spot/on-demand node groups, IRSA, KMS encryption
- RDS PostgreSQL with Multi-AZ, automated backups, enhanced monitoring
- Least-privilege IAM roles for EKS workloads (cluster-autoscaler, ALB controller)
- S3 + DynamoDB remote state with locking
- GitHub Actions pipeline using OIDC (zero long-lived AWS credentials)
- Architecture Decision Records explaining every major design choice

`Terraform` `AWS EKS` `AWS RDS` `IAM` `VPC` `GitHub Actions` `OIDC`

---

### 🚀 [cultivo-cicd-pipeline](https://github.com/atiladeoyetunji/cultivo-cicd-pipeline)
> *End-to-end CI/CD: code push → production in under 5 minutes*

A real pipeline with real gates. Shows how I think about deployment safety — vulnerability scanning before any image gets near production, zero-downtime rollouts, one-command rollbacks.

**What's inside:**
- Declarative Jenkinsfile with parallel lint/test stages, Trivy image scanning
- GitHub Actions: CI on PRs, CD on merge to main with OIDC-based ECR push
- Multi-stage Dockerfile (node:alpine final stage, non-root user, <150MB)
- Kubernetes deployment with rolling update strategy, liveness/readiness probes, HPA
- PodDisruptionBudget ensuring minimum availability during node drains
- `scripts/rollback.sh` — one command to revert any bad deploy

`Jenkins` `GitHub Actions` `Docker` `ECR` `EKS` `Trivy` `Kubernetes`

---

### ☸️ [kubernetes-production-setup](https://github.com/atiladeoyetunji/kubernetes-production-setup)
> *The K8s manifests I wish every cluster shipped with*

Most K8s clusters I've inherited had no network policies, overly-permissive RBAC, and no disruption budgets. This repo is the baseline I enforce before any workload goes to production.

**What's inside:**
- Default-deny NetworkPolicy model with explicit allow rules only
- Least-privilege RBAC: separate roles for devs, CI/CD, monitoring (no cluster-admin anywhere)
- Deployments with pod anti-affinity, securityContext (non-root, readOnlyRootFilesystem, drop ALL caps), topologySpreadConstraints
- HPA with CPU + memory + custom metrics
- TLS ingress via cert-manager + Let's Encrypt
- External Secrets Operator integration with AWS Secrets Manager
- Full parameterized Helm chart with production/staging values
- Architecture Decision Records (GitOps, External Secrets, Cilium)

`Kubernetes` `Helm` `RBAC` `NetworkPolicy` `cert-manager` `External Secrets` `HPA`

---

### 🐳 [docker-microservices](https://github.com/atiladeoyetunji/docker-microservices)
> *A real multi-service architecture — not a hello-world Compose file*

Three services (API + async worker + frontend), a database, a cache, and a reverse proxy — wired together correctly. The kind of local environment that mirrors production closely enough that "works on my machine" stops being an excuse.

**What's inside:**
- API service (Express.js with Prometheus metrics endpoint, structured JSON logging)
- Worker service (Redis queue processor with graceful SIGTERM handling)
- Frontend served via nginx with security headers and gzip compression
- docker-compose.yml (dev) + docker-compose.prod.yml (resource limits, restart policies)
- docker-compose.monitoring.yml (adds Prometheus + Grafana to the stack)
- Multi-stage Dockerfiles for all services (non-root, minimal attack surface)
- GitHub Actions: matrix build for all 3 images, multi-platform (amd64/arm64), push to GHCR

`Docker` `Docker Compose` `nginx` `Redis` `PostgreSQL` `GitHub Actions` `GHCR`

---

### 📊 [monitoring-stack](https://github.com/atiladeoyetunji/monitoring-stack)
> *Full observability — metrics, logs, alerts — deployable in 5 minutes*

Observability is not optional on systems I run. This is the stack I stand up before any workload goes live — with real alert rules, real Slack templates, and real runbooks written from actual on-call experience.

**What's inside:**
- Prometheus with 35+ alerting rules (node, application, Kubernetes) — valid PromQL, production-calibrated thresholds
- Alertmanager routing: critical → PagerDuty, warning → Slack, inhibit rules to suppress noise
- Grafana with auto-provisioned dashboards: RED method (Rate/Errors/Duration), node metrics, K8s cluster overview
- Loki + Promtail for log aggregation
- 6 runbooks with exact kubectl/curl commands (written after real incidents, not copied from docs)
- Kubernetes manifests for HA deployment (2 replicas each)
- `scripts/test-alerts.sh` to verify alert routing without waiting for a real incident

`Prometheus` `Grafana` `Alertmanager` `Loki` `Kubernetes` `PagerDuty` `PromQL`

---

## How These Repos Connect

```
┌─────────────────────────────────────────────────────────┐
│              cultivo-aws-infrastructure-terraform               │
│         (VPC · EKS Cluster · RDS · IAM · S3)           │
└────────────────────┬────────────────────────────────────┘
                     │ provisions cluster
          ┌──────────┴──────────┐
          ▼                     ▼
┌──────────────────┐   ┌─────────────────────┐
│  kubernetes-     │   │   monitoring-stack  │
│  production-     │   │  (Prometheus/Grafana │
│  setup           │   │   Loki/Alertmanager) │
│  (RBAC·NetworkP  │   │                     │
│   Ingress·HPA)   │   └─────────────────────┘
└────────┬─────────┘
         │ workloads deployed by
         ▼
┌──────────────────────┐     ┌────────────────────┐
│  cultivo-cicd-pipeline  │────▶│ docker-microservices│
│  (Jenkins/GH Actions │     │ (the apps that run  │
│   Build·Scan·Deploy) │     │  on the cluster)    │
└──────────────────────┘     └────────────────────┘
```

---

## What I'm Currently Building

- Production-grade DevOps tooling and infrastructure patterns
- AI-integrated automation systems (LLM-powered ops tooling)
- Platform engineering primitives for high-growth product teams
- Scaling infrastructure practices suitable for African tech ecosystems and global markets

---

## Philosophy

> **Reliability is a feature. Security is not optional. Automation is the only escape from toil.**

I've seen what happens when you skip the boring foundations — monitoring, runbooks, proper RBAC, tested rollbacks. You don't notice the missing foundation until 2am when everything is on fire.

The repos here reflect how I build when I have time to do it right. The goal is always: *could a competent engineer I've never met pick this up and operate it safely?*

---

<div align="center">

**Open to senior DevOps / Platform / Cloud infrastructure roles**

[![LinkedIn](https://img.shields.io/badge/Let's_connect_on_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/oyetunji-atilade)

</div>
