# GPM-37: All Services Identified in Repository

## Application Microservices
| Service | Folder | Port |
|---------|--------|------|
| config-server | spring-petclinic-config-server | 8888 |
| discovery-server | spring-petclinic-discovery-server | 8761 |
| api-gateway | spring-petclinic-api-gateway | 8080 |
| customers-service | spring-petclinic-customers-service | 8081 |
| vets-service | spring-petclinic-vets-service | 8083 |
| visits-service | spring-petclinic-visits-service | 8082 |
| admin-server | spring-petclinic-admin-server | 9090 |

## Supporting/Infrastructure Services
| Service | Port | Purpose |
|---------|------|---------|
| Prometheus | 9091 | Metrics collection |
| Grafana | 3030 | Metrics dashboards |
| Zipkin | 9411 | Distributed tracing |

## GenAI Service
| Service | Purpose |
|---------|---------|
| genai-service | OpenAI-powered AI chat assistant |

## Identified From
- Repository folder structure
- docker-compose.yml service definitions
- Osenat's README service table
