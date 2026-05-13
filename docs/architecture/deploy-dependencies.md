# GPM-66: Deployment Dependencies Per Service

## Infrastructure required before deployment
| Infrastructure | Required by | Created by |
|---------------|------------|-----------|
| VPC + subnets | EKS cluster | Terraform vpc module |
| EKS cluster | All services | Terraform eks module |
| ECR repositories | CI/CD pipeline | Terraform ecr module |
| RDS MySQL | customers, vets, visits | Terraform rds module |
| AWS Secrets Manager | ESO, genai | Terraform or manual |
| External Secrets Operator | mysql-secret | Helm install |
| AWS Load Balancer Controller | ALB Ingress | Helm install |

## Kubernetes deployment order
1. External Secrets Operator (namespace: external-secrets)
2. ClusterSecretStore
3. ExternalSecret (creates mysql-secret and genai-secret)
4. config-server
5. discovery-server
6. api-gateway + customers + vets + visits + admin + genai
7. ALB Ingress
8. Route 53 A record

## ArgoCD
After initial setup ArgoCD auto-deploys all changes
pushed to main branch of the platform repo.
