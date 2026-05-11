# GPM-34: Project README Review

## Source
Osenat Alonge (etaoko333) — Spring PetClinic Microservices AWS Production Deployment

## Key Setup Requirements Identified
- WSL2 Ubuntu machine
- AWS CLI configured
- Terraform >= 1.3.0
- kubectl
- Helm
- Docker
- Java 17
- Claude Code CLI (for infrastructure generation)

## Important Commands
- Local run:       docker compose up -d
- Build images:    ./mvnw clean install -P buildDocker -Dmaven.test.skip=true
- Connect cluster: aws eks update-kubeconfig --region us-east-1 --name petclinic-eks
- Check pods:      kubectl get pods -n petclinic

## Deployment Phases (from README)
- Phase A: Local Docker Compose testing
- Phase B: Terraform — VPC, EKS, ECR, RDS
- Phase C: Build and push Docker images to ECR
- Phase D: Secrets Manager + External Secrets Operator
- Phase E: Helm chart deployment
- Phase F: GitOps with ArgoCD
- Phase G: GitHub Actions CI/CD
- Phase H: ALB Ingress + Route 53 HTTPS
- Phase I: Prometheus + Grafana monitoring

## Two-Repo GitOps Pattern
- petclinic-microservices: app source code + CI pipeline
- petclinic-k8s-platform: Terraform + Helm + ArgoCD manifests
