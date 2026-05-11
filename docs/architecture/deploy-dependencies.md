# GPM-66: Deployment Dependencies Per Service

## Infrastructure that must exist before deployment

| Infrastructure | Required by | Provided by |
|---------------|------------|-------------|
| VPC + subnets | EKS cluster | Terraform vpc module |
| EKS cluster | All services | Terraform eks module |
| ECR repositories | CI/CD pipeline | Terraform ecr module |
| RDS MySQL | customers, vets, visits | Terraform rds module |
| AWS Secrets Manager | ESO, genai | Manual or Terraform |
| External Secrets Operator | mysql-secret, genai-secret | Helm install |
| AWS Load Balancer Controller | ALB Ingress | Helm install |

## Deployment order in Kubernetes

1. External Secrets Operator (namespace: external-secrets)
2. ClusterSecretStore (connects ESO to Secrets Manager)
3. ExternalSecret (creates mysql-secret and genai-secret)
4. config-server deployment
5. discovery-server deployment
6. api-gateway + customers + vets + visits + admin + genai deployments
7. ALB Ingress (creates the load balancer)
8. Route 53 A record (points domain to ALB)

## Helm chart deployment command
helm upgrade --install petclinic helm/petclinic/ \
  --namespace petclinic \
  --set image.registry=ACCOUNT.dkr.ecr.us-east-1.amazonaws.com \
  --set image.tag=latest

## ArgoCD auto-sync
After initial setup ArgoCD watches the platform repo and
automatically deploys any changes pushed to main.
