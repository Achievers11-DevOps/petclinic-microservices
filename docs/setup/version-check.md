# GPM-36: Tool Version Verification

## Commands Run
java --version
./mvnw --version
git --version
docker --version
docker compose version

## Expected Minimum Versions
| Tool | Minimum Version |
|------|----------------|
| Java | 17 |
| Maven | 3.9.x |
| Git | 2.x |
| Docker | 24.x |
| Docker Compose | 2.x |
| Terraform | 1.3.0 |
| kubectl | 1.32.x |
| eksctl | 0.180.x |

## Notes
- Java must be version 17 exactly — Spring Boot 3.x requires it
- Docker Compose v2 uses 'docker compose' not 'docker-compose'
- Terraform must be >= 1.3.0 as required by Osenat's README
