# GPM-42 GPM-53: All Microservices and Service Ports

## Application Microservices
| Service | Folder | Port | Purpose |
|---------|--------|------|---------|
| config-server | spring-petclinic-config-server | 8888 | Centralised configuration for all services |
| discovery-server | spring-petclinic-discovery-server | 8761 | Eureka service registry |
| api-gateway | spring-petclinic-api-gateway | 8080 | Public entry point, routes all client requests |
| customers-service | spring-petclinic-customers-service | 8081 | Owner and pet management — MySQL |
| vets-service | spring-petclinic-vets-service | 8083 | Veterinarian data — MySQL |
| visits-service | spring-petclinic-visits-service | 8082 | Pet visit records — MySQL |
| admin-server | spring-petclinic-admin-server | 9090 | Spring Boot Admin dashboard |
| genai-service | spring-petclinic-genai-service | 8084 | OpenAI/Azure AI powered chat assistant |

## Supporting/Monitoring Services
| Service | Port | Purpose |
|---------|------|---------|
| Prometheus | 9091 | Metrics collection from all services |
| Grafana | 3030 | Metrics visualisation dashboards |
| Zipkin (tracing-server) | 9411 | Distributed tracing across services |

## Notes
- All services expose /actuator/health for health checks
- All services expose /actuator/prometheus for metrics
- Only api-gateway is publicly accessible
- All other services are internal only
