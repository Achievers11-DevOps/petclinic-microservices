# GPM-61: Service Health Check Endpoints

## Spring Boot Actuator Endpoints
All PetClinic microservices use Spring Boot Actuator for health checks.

| Endpoint | Purpose |
|----------|---------|
| /actuator/health | Overall health status — used by Docker/Kubernetes |
| /actuator/info | Service information |
| /actuator/metrics | Application metrics |
| /actuator/prometheus | Prometheus-format metrics (scraped by Prometheus) |

## Health check per service
| Service | Health URL |
|---------|-----------|
| config-server | http://localhost:8888/actuator/health |
| discovery-server | http://localhost:8761/actuator/health |
| api-gateway | http://localhost:8080/actuator/health |
| customers-service | http://localhost:8081/actuator/health |
| vets-service | http://localhost:8083/actuator/health |
| visits-service | http://localhost:8082/actuator/health |
| admin-server | http://localhost:9090/actuator/health |
| genai-service | http://localhost:8084/actuator/health |

## How Docker Compose uses health checks
- config-server: healthcheck runs every 10s
- Other services use depends_on condition: service_healthy
- Kubernetes: uses readinessProbe and livenessProbe on /actuator/health

## Expected response when healthy
{"status":"UP"}
