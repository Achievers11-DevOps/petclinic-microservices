# GPM-68: Service Dependency Diagram

## Startup Dependencies
## Runtime Dependencies
## Infrastructure Dependencies
## Failure impact analysis
| Service fails | Impact |
|--------------|--------|
| config-server | All other services cannot start |
| discovery-server | api-gateway cannot route requests |
| api-gateway | Application completely inaccessible |
| customers-service | Owners and pets features unavailable |
| vets-service | Vets listing unavailable |
| visits-service | Visit records unavailable |
| genai-service | AI chat unavailable, rest of app works |
| RDS MySQL | customers, vets, visits all fail |
