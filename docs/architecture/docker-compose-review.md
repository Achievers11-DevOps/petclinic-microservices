# GPM-57: Docker Compose Architecture Review

## Services defined in docker-compose.yml
| Container name | Image | Ports |
|----------------|-------|-------|
| config-server | springcommunity/spring-petclinic-config-server | 8888 |
| discovery-server | springcommunity/spring-petclinic-discovery-server | 8761 |
| api-gateway | springcommunity/spring-petclinic-api-gateway | 8080 |
| customers-service | springcommunity/spring-petclinic-customers-service | 8081 |
| vets-service | springcommunity/spring-petclinic-vets-service | 8083 |
| visits-service | springcommunity/spring-petclinic-visits-service | 8082 |
| admin-server | springcommunity/spring-petclinic-admin-server | 9090 |
| genai-service | springcommunity/spring-petclinic-genai-service | 8084 |
| grafana-server | petclinic-microservices-grafana-server | 3030 |
| prometheus-server | petclinic-microservices-prometheus-server | 9091 |
| tracing-server | openzipkin/zipkin | 9411 |

## Network
All containers share one Docker network: petclinic-microservices_default
Services reference each other by container name as hostname.

## Startup dependencies (depends_on)
- discovery-server depends on: config-server (healthy)
- All app services depend on: config-server (healthy) + discovery-server (healthy)

## Volumes
- grafana-server: grafana data persistence
- prometheus-server: prometheus data persistence

## Environment variables set by Docker Compose
- SPRING_PROFILES_ACTIVE=docker
- EUREKA_CLIENT_SERVICEURL_DEFAULTZONE=http://discovery-server:8761/eureka/
- CONFIG_SERVER_URL=http://config-server:8888
