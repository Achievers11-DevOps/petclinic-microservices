# GPM-55: External Access Points

## User-facing entry points
| URL | Service | Access |
|-----|---------|--------|
| https://eta-oko.com | api-gateway via ALB | Public |
| http://localhost:8080 | api-gateway | Local only |

## Admin and monitoring access points
| URL | Service | Access |
|-----|---------|--------|
| http://localhost:8761 | Eureka dashboard | Local only |
| http://localhost:9090 | Spring Boot Admin | Local only |
| http://localhost:3030 | Grafana | Local only |
| http://localhost:9091 | Prometheus | Local only |
| http://localhost:9411 | Zipkin | Local only |

## Production monitoring
- Grafana: exposed via LoadBalancer service in monitoring namespace
- Prometheus: internal only, scraped by Grafana
- Zipkin: exposed via LoadBalancer in petclinic namespace
- ArgoCD: exposed via LoadBalancer in argocd namespace

## Security note
Only api-gateway is exposed to the internet.
All monitoring and admin tools are internal or behind VPN in production.
