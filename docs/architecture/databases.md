# GPM-58: Databases and Data Storage Per Service

## Service to Database Mapping
| Service | Database | Tables | Notes |
|---------|----------|--------|-------|
| customers-service | MySQL/H2 | owners, pets, types | Owner and pet data |
| vets-service | MySQL/H2 | vets, specialities, vet_specialities | Vet data |
| visits-service | MySQL/H2 | visits | Visit records |
| api-gateway | None | — | Stateless router |
| config-server | None | — | Reads from filesystem/git |
| discovery-server | None | — | In-memory registry |
| admin-server | None | — | Reads from actuator endpoints |
| genai-service | None | — | Stateless AI proxy |

## Local environment
- Database: H2 in-memory
- Data resets on every container restart
- No persistence between sessions

## Production environment (AWS)
- Database: Amazon RDS MySQL 8.0
- Instance: db.t3.micro
- Persistent across restarts
- Credentials stored in AWS Secrets Manager
- Synced to Kubernetes via External Secrets Operator as mysql-secret

## Database credentials in production
- MYSQL_HOST — RDS endpoint
- MYSQL_USER — petclinic
- MYSQL_PASSWORD — from Secrets Manager
- MYSQL_DATABASE — petclinic
