# GPM-61: Service Health Check Endpoints

## Spring Boot Actuator endpoints (all services)
| Endpoint | Purpose |
|----------|---------|
| /actuator/health | Overall health — used by Docker and Kubernetes |
| /actuator/prometheus | Metrics scraped by Prometheus every 15s |
| /actuator/info | Service information |

## Health URLs per service
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

## Expected healthy response
{"status":"UP"}

## Kubernetes probes
- readinessProbe: /actuator/health (is service ready to receive traffic?)
- livenessProbe: /actuator/health (is service still alive?)
