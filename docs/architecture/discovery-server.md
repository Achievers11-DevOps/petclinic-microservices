# GPM-45: Discovery Server Purpose and Service Registration

## Purpose
Eureka service registry. All microservices register here on startup
so other services can find them by name without hardcoded URLs.

## Port
8761

## How service registration works
1. discovery-server starts and becomes available
2. Each service starts and sends a registration request:
   POST http://discovery-server:8761/eureka/apps/{SERVICE-NAME}
3. discovery-server records the service name, IP, port, and health status
4. api-gateway queries discovery-server to find where to route requests
5. Services send heartbeats every 30 seconds to stay registered

## Eureka dashboard
http://localhost:8761 — shows all registered services and their status

## Services registered in Eureka
- api-gateway
- customers-service
- vets-service
- visits-service
- admin-server
- genai-service

## Startup dependency
discovery-server depends on config-server being healthy first.
All other services depend on discovery-server being healthy.
