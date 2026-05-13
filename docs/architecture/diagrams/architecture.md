# GPM-67: Architecture Diagram

## System Architecture — Text Diagram
## Component Roles
| Component | Role |
|-----------|------|
| ALB | Public entry, SSL, HTTP→HTTPS redirect |
| api-gateway | Request routing, service discovery |
| config-server | Centralised configuration |
| discovery-server | Service registry (Eureka) |
| customers/vets/visits | Business logic + MySQL data |
| genai-service | AI chat via Azure OpenAI |
| Prometheus + Grafana | Metrics and dashboards |
| Zipkin | Distributed request tracing |
