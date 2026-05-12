# GPM-200: PetClinic Microservices — Master Architecture Documentation

## Primary assignee
Odi Chibuzor Greg — Technical Lead (gregodprogrammer)

## Overview
This is the master index for all PetClinic Microservices architecture
documentation. All architecture files live in this docs/architecture/ folder.

## Quick Reference
Production URL: https://eta-oko.com
Local: docker compose up -d then open http://localhost:8080

## Architecture Documents Index

### Core Architecture
| File | Ticket | Contents |
|------|--------|---------|
| overview.md | GPM-41 GPM-7 | Overall architecture and CI/CD flow |
| services.md | GPM-42 GPM-53 | All 8 services, ports, purposes |
| startup-order.md | GPM-52 | Correct startup sequence |
| api-gateway.md | GPM-43 | API Gateway routing and role |
| config-server.md | GPM-44 | Config Server and configuration flow |
| discovery-server.md | GPM-45 | Eureka service registry |

### Domain Services
| File | Ticket | Contents |
|------|--------|---------|
| customers-service.md | GPM-48 | Owner and pet management |
| vets-service.md | GPM-49 | Veterinarian data |
| visits-service.md | GPM-50 | Pet visit records |
| genai-service.md | GPM-51 | AI chat via Azure OpenAI |

### Infrastructure and Configuration
| File | Ticket | Contents |
|------|--------|---------|
| databases.md | GPM-58 | Database per service mapping |
| env-vars-secrets.md | GPM-59 | Environment variables and secrets |
| health-checks.md | GPM-61 | Health check endpoints |
| logging.md | GPM-62 | Logging approach |
| config-files.md | GPM-56 | Application config files |
| docker-compose-review.md | GPM-57 | Docker Compose structure |

### Network and Access
| File | Ticket | Contents |
|------|--------|---------|
| communication.md | GPM-54 | Service communication map |
| access-points.md | GPM-55 | External and internal access points |

### Security and Risk
| File | Ticket | Contents |
|------|--------|---------|
| security.md | GPM-65 | Security architecture review |
| risks.md | GPM-72 | Architecture risks and assumptions |
| deploy-dependencies.md | GPM-66 | Deployment dependencies |

### Diagrams
| File | Ticket | Contents |
|------|--------|---------|
| diagrams/architecture.md | GPM-67 | Full system architecture diagram |
| diagrams/dependencies.md | GPM-68 | Service dependency diagram |

### Team Guides
| File | Ticket | Contents |
|------|--------|---------|
| walkthrough.md | GPM-74 | Architecture walkthrough for team |

## Service Summary
| Service | Port | Starts | Database | Public |
|---------|------|--------|---------|--------|
| config-server | 8888 | 1st | None | No |
| discovery-server | 8761 | 2nd | None | No |
| api-gateway | 8080 | 3rd | None | Yes via ALB |
| customers-service | 8081 | 3rd | MySQL/RDS | No |
| vets-service | 8083 | 3rd | MySQL/RDS | No |
| visits-service | 8082 | 3rd | MySQL/RDS | No |
| admin-server | 9090 | 3rd | None | No |
| genai-service | 8084 | 3rd | None | No |

## AWS Infrastructure Summary
| Resource | Name | Details |
|----------|------|---------|
| Region | us-east-1 | N. Virginia |
| EKS Cluster | petclinic-eks | Kubernetes 1.32 |
| Node Group | 2x t3.small | min 1, max 3 |
| ECR | 8 repositories | One per service |
| RDS | petclinic-mysql | MySQL 8.0, db.t3.micro |
| ALB | Auto-created | Via LB Controller |
| Domain | eta-oko.com | Route 53 and ACM |

## Startup Order Critical
1. config-server port 8888 MUST start first
2. discovery-server port 8761 starts second after config-server healthy
3. All others start together after discovery-server healthy
Wrong startup order causes cascading failures across all services.

## Monitoring Stack
| Tool | Port | Purpose |
|------|------|---------|
| Prometheus | 9091 | Scrapes /actuator/prometheus every 15s |
| Grafana | 3030 | Dashboards admin/admin locally |
| Zipkin | 9411 | Distributed tracing |

## Key Architecture Decisions
1. Single public entry point — only api-gateway exposed via ALB
2. config-server is critical — single point of failure at startup
3. Secrets never hardcoded — Secrets Manager plus ESO pattern
4. GitOps via ArgoCD — cluster always matches repo state
5. Two-repo pattern — app concerns separated from infra concerns
6. Database per service — no cross-service database access
7. H2 locally MySQL in production — Spring profile switching

## How to Navigate This Documentation
New to the project? Read in this order:
1. overview.md — understand the big picture
2. services.md — know what each service does
3. startup-order.md — understand why order matters
4. diagrams/architecture.md — see the full system
5. walkthrough.md — team presentation guide
