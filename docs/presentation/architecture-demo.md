# GPM-212: Architecture Demo Section

## Demo Overview
Presenter: Odi Chibuzor Greg — Technical Lead
Duration: 3 minutes
Section: Architecture walkthrough for final presentation

## Pre-Demo Setup
Have these open in browser before presenting:
- Tab 1: docs/architecture/diagrams/architecture.md
- Tab 2: https://eta-oko.com (live application)
- Tab 3: Eureka dashboard
- Tab 4: GitHub repo Achievers11-DevOps/petclinic-microservices

## Demo Script

### Opening (30 seconds)
SAY: The PetClinic application is not one application.
SAY: It is 8 separate microservices each doing one job.
SAY: Let me show you how they work together.

### Show the architecture diagram (60 seconds)
DO: Open docs/architecture/diagrams/architecture.md
SAY: Every user request starts at the internet.
SAY: It hits the AWS Load Balancer which handles HTTPS.
SAY: The Load Balancer forwards to api-gateway on port 8080.
SAY: api-gateway is the only service exposed to the internet.
SAY: Everything else is internal ClusterIP only.
SAY: config-server starts first — it holds all configuration.
SAY: Nothing else can start until config-server is healthy.
SAY: discovery-server starts second — it is the service directory.
SAY: api-gateway asks discovery-server where to route each request.

### Show the live application (45 seconds)
DO: Open https://eta-oko.com
SAY: This is running live on AWS EKS right now.
SAY: When you click Find Owners that request goes to api-gateway.
SAY: api-gateway routes it to customers-service on port 8081.
SAY: customers-service queries RDS MySQL and returns the data.
DO: Click Find Owners to show the flow working live.

### Show the two-repo pattern (30 seconds)
DO: Open GitHub repo
SAY: We use two repositories — app code and infrastructure.
SAY: When code is pushed to main GitHub Actions builds Docker images.
SAY: ArgoCD watches the platform repo and deploys to EKS automatically.
SAY: Zero manual deployments. Push code — application updates.

### Closing (15 seconds)
SAY: 8 services, fully automated CI/CD, production on AWS.
SAY: config-server starts first. Everything else follows.

## Key Points to Emphasise
1. Single public entry point — api-gateway only
2. config-server is critical — must start first
3. Secrets never hardcoded — AWS Secrets Manager
4. GitOps via ArgoCD — cluster matches repo at all times
5. Two-repo pattern — app code separate from infrastructure

## Backup Plan if Live Demo Fails
If eta-oko.com is down:
DO: Switch to local Docker Compose screenshots
DO: Show docker compose ps — all 11 containers running
DO: Show localhost-8080 screenshot — app running locally
SAY: Same application running locally with Docker Compose.

## Evidence Screenshots Needed Before Presentation Day
- architecture-diagram-text.png
- live-app-eta-oko.png
- eureka-all-services-registered.png
- github-actions-green-build.png
- argocd-synced-healthy.png
