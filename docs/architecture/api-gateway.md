# GPM-43: API Gateway Role and Routing

## Purpose
The API Gateway is the single public entry point for all client requests.
No client ever calls backend services directly.

## Port
8080 (locally) — 80/443 in production via ALB

## How it works
1. Client sends request to api-gateway
2. api-gateway looks up the target service in Eureka (discovery-server)
3. Routes the request to the correct backend service
4. Returns the response to the client

## Services routed through api-gateway
| Route | Target Service |
|-------|---------------|
| /api/customer/** | customers-service |
| /api/vet/** | vets-service |
| /api/visit/** | visits-service |
| /api/gateway/** | api-gateway itself |

## Technology
Spring Cloud Gateway — reactive, non-blocking

## Key dependency
- Requires discovery-server to be running and healthy
- Requires config-server for its own configuration

## Production setup
- Sits behind AWS ALB (Application Load Balancer)
- ALB handles SSL termination (HTTPS)
- ALB routes all traffic to api-gateway on port 8080
- api-gateway routes internally to services
