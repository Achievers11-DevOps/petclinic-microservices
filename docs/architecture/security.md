# GPM-65: Security Architecture Review

## Publicly exposed services
| Service | Exposure | Method |
|---------|----------|--------|
| api-gateway | Public | ALB port 80/443 |
| All others | Internal | ClusterIP only |

## Secret management
| Secret | Storage | How accessed |
|--------|---------|-------------|
| DB credentials | AWS Secrets Manager | ESO → K8s secret |
| OpenAI key | AWS Secrets Manager | ESO → K8s secret |
| GitHub tokens | GitHub Secrets | GitHub Actions only |

## Security risks
| Risk | Severity | Mitigation |
|------|----------|-----------|
| No API authentication | Medium | Acceptable for demo |
| H2 console exposed locally | Low | Local dev only |
| Single api-gateway replica | Medium | Add replica in production |
| Admin endpoints public | Medium | Restrict to internal only |

## Recommendations for production
- Add JWT/OAuth2 authentication to api-gateway
- Enable AWS WAF on the ALB
- Restrict admin-server to internal network
- Enable HTTPS for internal service communication
- Rotate all secrets every 90 days
