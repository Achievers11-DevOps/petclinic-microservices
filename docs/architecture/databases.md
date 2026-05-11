# GPM-58: Databases and Data Storage Per Service

## Service to Database Mapping
| Service | Database | Tables |
|---------|----------|--------|
| customers-service | MySQL/H2 | owners, pets, types |
| vets-service | MySQL/H2 | vets, specialities, vet_specialities |
| visits-service | MySQL/H2 | visits |
| api-gateway | None | stateless router |
| config-server | None | reads from filesystem |
| discovery-server | None | in-memory registry |
| admin-server | None | reads actuator endpoints |
| genai-service | None | stateless AI proxy |

## Local environment
- H2 in-memory database
- Data resets on every container restart
- No persistence between sessions

## Production environment
- Amazon RDS MySQL 8.0 (db.t3.micro)
- Persistent across restarts
- Credentials from AWS Secrets Manager via ESO

## Database credentials in Kubernetes
- MYSQL_HOST — RDS endpoint
- MYSQL_USER — petclinic
- MYSQL_PASSWORD — from Secrets Manager
- MYSQL_DATABASE — petclinic
