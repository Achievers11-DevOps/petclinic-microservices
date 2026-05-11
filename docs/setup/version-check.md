# GPM-36: Tool Version Verification — Greg's Machine

## Command Run
java --version && ./mvnw --version && git --version && docker --version && docker compose version

## Verified Versions on Greg's Machine (WSL2 Ubuntu)
| Tool | Version | Requirement | Status |
|------|---------|-------------|--------|
| Java | 17.0.18 OpenJDK | 17 | Pass |
| Maven | 3.9.8 | 3.9.x | Pass |
| Git | 2.34.1 | 2.x | Pass |
| Docker | 29.4.2 | 24.x minimum | Pass |
| Docker Compose | v5.1.3 | v2 | Pass |

## Notes
- Java 17 confirmed — required for Spring Boot 3.x
- Docker Compose v5.1.3 uses 'docker compose' command not 'docker-compose'
- All tools verified on WSL2 Ubuntu 22.04
