# GPM-74: Architecture Walkthrough — Team Guide

## Purpose
This document provides a structured walkthrough of the PetClinic
microservices architecture for team knowledge sharing and presentation.

## Walkthrough sequence

### 1. Start with the user journey
A user opens https://eta-oko.com in their browser.
The request hits the AWS ALB which terminates SSL and forwards to api-gateway.
api-gateway looks up the target service in Eureka and routes the request.
The response travels back through api-gateway to the user.

### 2. Show the startup sequence
config-server must be healthy before anything else starts.
discovery-server starts next and registers with itself.
All other services start and register with discovery-server.
Only after registration does api-gateway know where to route requests.

### 3. Explain configuration management
Every service fetches its config from config-server on startup.
Config profiles control which database to use (H2 locally, MySQL in prod).
Secrets never appear in config files — they come from Secrets Manager via ESO.

### 4. Walk through the database setup
Three services use MySQL: customers, vets, visits.
Each has its own schema — no cross-service database access.
Locally: H2 in-memory (data resets on restart).
Production: RDS MySQL (persistent, managed by AWS).

### 5. Explain the CI/CD pipeline
Developer pushes to feature branch → Greg Branch CI runs → build validates.
PR to dev → CI runs again → reviewer approves → merges to dev.
PR to main → CI runs → Osenat approves → merges to main.
GitHub Actions builds Docker image → pushes to ECR with SHA tag.
Updates image tag in platform repo → ArgoCD detects → deploys to EKS.

### 6. Show monitoring
Prometheus scrapes /actuator/prometheus on all services every 15 seconds.
Grafana displays dashboards (Spring Boot Observability, Kubernetes overview).
Zipkin shows distributed traces across service calls.

## Key points to emphasise in presentation
- Single point of entry (api-gateway) — good security practice
- config-server is critical — single point of failure to acknowledge
- Secrets never hardcoded — Secrets Manager + ESO pattern
- GitOps — ArgoCD ensures cluster state matches repo state
- Two-repo pattern separates app concerns from infrastructure concerns
