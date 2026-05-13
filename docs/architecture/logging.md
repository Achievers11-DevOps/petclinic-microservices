# GPM-62: Logging Approach

## How services produce logs
All services use Spring Boot default logging (Logback).
Logs are written to stdout (console) — not to files.

## Log levels
| Level | When used |
|-------|----------|
| INFO | Normal operation, startup messages |
| WARN | Non-critical issues (missing optional config) |
| ERROR | Failures that need attention |
| DEBUG | Detailed debugging (disabled in production) |

## Useful logs to check per service
| Service | What to look for |
|---------|-----------------|
| config-server | Started ConfigServerApplication |
| discovery-server | Started EurekaApplication, Changing status to UP |
| api-gateway | Started ReactiveWebServerApplicationContext |
| All services | Started [ServiceName]Application |

## How to view logs locally
docker logs config-server --tail=50
docker logs discovery-server --tail=50
docker compose logs --follow

## Production log aggregation
Fluent Bit runs as DaemonSet on each EKS node.
Collects logs from all pods and forwards to CloudWatch Logs.

## Common log patterns that indicate problems
- Connection refused to config-server → config-server not ready yet
- Unable to connect to Eureka → discovery-server not ready yet
- AZURE_OPENAI_KEY not set → expected warning, not an error
