# GPM-52: Correct Service Startup Order

## Startup Sequence — CRITICAL
Wrong startup order causes cascading failures across all services.

### Order
1. config-server (port 8888)
   - MUST start first
   - All other services fetch configuration from here on startup
   - If config-server is down, NO other service can start

2. discovery-server (port 8761)
   - Starts second
   - Services register here so they can find each other
   - api-gateway needs this to route requests

3. All remaining services start together (in any order):
   - api-gateway (8080)
   - customers-service (8081)
   - vets-service (8082)
   - visits-service (8083)
   - admin-server (9090)
   - genai-service (8084)

## Supporting services (start anytime)
- prometheus, grafana, zipkin — independent, no dependency on app services

## How Docker Compose handles this
- Uses depends_on with healthcheck condition
- config-server healthcheck: /actuator/health must return UP
- discovery-server waits for config-server to be healthy
- All app services wait for both config-server and discovery-server

## Startup times on WSL2 Ubuntu (observed)
| Service | Startup time |
|---------|-------------|
| config-server | ~30 seconds |
| discovery-server | ~194 seconds |
| api-gateway | ~45 seconds |
| domain services | ~60 seconds each |

## Risk of wrong startup order
- Services fail to fetch config → crash on startup
- Services cannot register with Eureka → api-gateway cannot route
- All dependent services show unhealthy until config-server is ready
