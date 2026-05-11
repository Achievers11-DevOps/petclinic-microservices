# GPM-54: Service Communication Map

## External to Internal Flow
Client → ALB (443) → api-gateway (8080) → backend services

## Service to Service Communication
| From | To | Method |
|------|----|--------|
| Client browser | api-gateway | HTTP/HTTPS |
| api-gateway | customers-service | HTTP via Eureka |
| api-gateway | vets-service | HTTP via Eureka |
| api-gateway | visits-service | HTTP via Eureka |
| api-gateway | genai-service | HTTP via Eureka |
| All services | config-server | HTTP on startup |
| All services | discovery-server | HTTP heartbeat every 30s |
| All services | zipkin | HTTP trace data |

## No direct database sharing
Each service owns its own database schema.
Services never access another service's database directly.

## Communication type
Synchronous REST HTTP — no message queues in this version.
