# GPM-59: Environment Variables and Secrets

## Required Environment Variables Per Service

### customers-service, vets-service, visits-service
| Variable | Source | Value |
|----------|--------|-------|
| SPRING_PROFILES_ACTIVE | docker-compose.yml | docker,mysql |
| MYSQL_HOST | Kubernetes secret: mysql-secret | RDS endpoint |
| MYSQL_USER | Kubernetes secret: mysql-secret | petclinic |
| MYSQL_PASSWORD | Kubernetes secret: mysql-secret | from Secrets Manager |
| MYSQL_DATABASE | Kubernetes secret: mysql-secret | petclinic |

### genai-service
| Variable | Source | Value |
|----------|--------|-------|
| AZURE_OPENAI_KEY | Kubernetes secret: genai-secret | from Secrets Manager |
| AZURE_OPENAI_ENDPOINT | Kubernetes secret: genai-secret | Azure endpoint URL |

## AWS Secrets Manager secrets
| Secret name | Contents |
|-------------|----------|
| petclinic/db-credentials | username, password, endpoint, port, dbname |
| petclinic/openai-api-key | OpenAI or Azure OpenAI API key |

## GitHub Actions secrets required
| Secret | Purpose |
|--------|---------|
| AWS_ACCESS_KEY_ID | ECR login and EKS deploy |
| AWS_SECRET_ACCESS_KEY | ECR login and EKS deploy |
| AWS_REGION | us-east-1 |
| AWS_ACCOUNT_ID | ECR registry URL construction |
| PLATFORM_REPO_PAT | Push image tag to platform repo |

## Security rules
- Never hardcode secrets in code or config files
- Never commit secrets to GitHub
- Always use Secrets Manager + ESO in production
- Rotate keys immediately if accidentally exposed
