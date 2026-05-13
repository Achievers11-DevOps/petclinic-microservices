# GPM-72: Architecture Risks and Assumptions

## Risks
| Risk | Impact | Likelihood | Mitigation |
|------|--------|-----------|-----------|
| config-server is single point of failure | High | Medium | Add replica, use retry logic |
| discovery-server slow startup on WSL2 | Medium | High | Allow 3-5 minutes on startup |
| OpenAI rate limits affect genai-service | Low | Medium | Use demo key for testing only |
| H2 data loss on container restart | Medium | High | Expected locally, use RDS in prod |
| Wrong startup order causes failures | High | Medium | Docker Compose handles via depends_on |
| EKS costs if cluster not deleted | High | High | Delete cluster after every session |

## Assumptions
- Docker Compose handles startup order correctly via healthchecks
- All services can reach config-server within 60 seconds of it becoming healthy
- RDS MySQL is accessible from EKS nodes via security group rules
- ACM certificate is valid and auto-renews
- Route 53 DNS propagation completes within 5 minutes

## Known limitations
- No service mesh (no mTLS between services)
- No circuit breaker implemented
- No API rate limiting on api-gateway
- Single region deployment (us-east-1)
- No multi-AZ RDS (cost saving for demo)
