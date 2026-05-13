# GPM-59: Environment Variables and Secrets Required

## MySQL services (customers, vets, visits)
| Variable | Source |
|----------|--------|
| SPRING_PROFILES_ACTIVE | docker-compose.yml (docker,mysql) |
| MYSQL_HOST | Kubernetes secret: mysql-secret |
| MYSQL_USER | Kubernetes secret: mysql-secret |
| MYSQL_PASSWORD | Kubernetes secret: mysql-secret |
| MYSQL_DATABASE | Kubernetes secret: mysql-secret |

## GenAI service
| Variable | Source |
|----------|--------|
| AZURE_OPENAI_KEY | Kubernetes secret: genai-secret |
| AZURE_OPENAI_ENDPOINT | Kubernetes secret: genai-secret |

## AWS Secrets Manager
| Secret name | Contents |
|-------------|----------|
| petclinic/db-credentials | username, password, endpoint, port, dbname |
| petclinic/openai-api-key | Azure OpenAI API key |

## GitHub Actions secrets
| Secret | Purpose |
|--------|---------|
| AWS_ACCESS_KEY_ID | ECR and EKS access |
| AWS_SECRET_ACCESS_KEY | ECR and EKS access |
| AWS_REGION | us-east-1 |
| AWS_ACCOUNT_ID | ECR registry URL |
| PLATFORM_REPO_PAT | Push image tag to platform repo |

## Security rules
- Never hardcode secrets in code
- Never commit secrets to GitHub
- Always use Secrets Manager in production
- Rotate keys immediately if exposed
