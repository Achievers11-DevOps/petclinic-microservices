# GPM-41 GPM-7: PetClinic Microservices — Overall Architecture Overview

## What is PetClinic Microservices?
Spring PetClinic Microservices is a distributed version of the classic
Spring PetClinic application. It demonstrates how to decompose a monolithic
application into independently deployable microservices.

## Architecture style
Microservices architecture with:
- Service discovery (Eureka)
- Centralised configuration (Config Server)
- API Gateway pattern
- Distributed tracing (Zipkin)
- Metrics and monitoring (Prometheus + Grafana)
- GitOps deployment (ArgoCD)
- Container orchestration (Kubernetes on AWS EKS)

## High level architecture
## Two-repo GitOps pattern
- petclinic-microservices — application source code + CI pipeline
- petclinic-k8s-platform  — Terraform + Helm + ArgoCD manifests

## CI/CD flow
1. Developer pushes to feature branch
2. GitHub Actions builds and pushes Docker image to ECR
3. GitHub Actions updates image tag in platform repo
4. ArgoCD detects change and deploys to EKS automatically

## Infrastructure (AWS)
- EKS cluster (us-east-1) — Kubernetes orchestration
- ECR — private Docker image registry
- RDS MySQL — managed database
- ALB — public load balancer with SSL
- Route 53 — DNS (eta-oko.com)
- ACM — SSL certificate (auto-renews)
- Secrets Manager — credential storage
- External Secrets Operator — syncs secrets to Kubernetes
