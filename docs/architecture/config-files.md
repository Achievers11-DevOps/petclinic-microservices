# GPM-56: Application Configuration Files Review

## Configuration file locations
Each service has configuration in:
spring-petclinic-{service}/src/main/resources/

## Key configuration files
| File | Purpose |
|------|---------|
| application.yml | Default configuration for all environments |
| application-docker.yml | Docker Compose specific config |
| bootstrap.yml | Config server connection settings |

## Important settings in application.yml
- spring.application.name — service name used for Eureka registration
- server.port — port the service listens on
- eureka.client.serviceUrl.defaultZone — discovery server URL
- spring.config.import — config server URL

## Environment-specific profiles
| Profile | When used | Database |
|---------|----------|---------|
| default | Local Maven run | H2 in-memory |
| docker | Docker Compose | H2 in-memory |
| mysql | Production Kubernetes | RDS MySQL |

## Config server configuration
All services fetch config from:
http://config-server:8888/{application}/{profile}

## Docker Compose environment variables
Set in docker-compose.yml:
- SPRING_PROFILES_ACTIVE=docker
- EUREKA_CLIENT_SERVICEURL_DEFAULTZONE=http://discovery-server:8761/eureka/
