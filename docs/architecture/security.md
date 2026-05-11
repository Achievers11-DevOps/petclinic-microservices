# GPM-65: Security Architecture Review

## Exposed Services (publicly accessible)
| Service | Exposure | How |
|---------|----------|-----|
| api-gateway | Public | Via ALB on port 80/443 |
| All others | Internal only | ClusterIP — not accessible outside cluster |

## Sensitive configuration areas
- Database credentials — stored in AWS Secrets Manager, never in code
- OpenAI API key — stored in AWS Secrets Manager, never in code
- GitHub Actions secrets — stored in GitHub, never in code or logs
- Kubernetes secrets — created by External Secrets Operator from Secrets Manager

## Security risks identified
| Risk | Severity | Mitigation |
|------|----------|-----------|
| Hardcoded secrets | High | Use Secrets Manager always |
| Exposed admin endpoints | Medium | Admin server behind VPN or internal only |
| H2 console exposed locally | Low | Only in local dev, not in production |
| No authentication on APIs | Medium | Acceptable for demo, add in production |
| Single api-gateway | Medium | Add replica in production |

## Recommendations
- Add API authentication (JWT/OAuth2) for production
- Enable HTTPS on all internal service communication
- Restrict admin-server to internal network only
- Enable AWS WAF on the ALB
- Regular rotation of all secrets
