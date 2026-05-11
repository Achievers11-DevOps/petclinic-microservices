# GPM-40: Local Setup Summary for the Team

## Quick Start — Run the App Locally in 3 Commands
sudo service docker start
cd ~/petclinic-microservices
docker compose up -d

## Wait 3-5 minutes then open:
http://localhost:8080  — PetClinic main app (start here)
http://localhost:8761  — Eureka (confirm all services registered)
http://localhost:9090  — Admin Server
http://localhost:3030  — Grafana (login: admin / admin)
http://localhost:9091  — Prometheus
http://localhost:9411  — Zipkin

## If Containers Conflict (old session containers present)
docker compose down --remove-orphans
docker container prune -f
docker compose up -d

## Stop When Done
docker compose down

## Required Tools
| Tool | Minimum Version | Install |
|------|----------------|---------|
| Docker | 24.x | sudo apt install docker.io |
| Docker Compose | v2 | sudo apt install docker-compose-v2 |
| Java | 17 | sudo apt install openjdk-17-jdk |
| Git | 2.x | sudo apt install git |

## Important Notes for the Team
- config-server MUST be healthy before other services start
- discovery-server takes up to 3 minutes on WSL2 — this is normal
- AZURE_OPENAI_KEY warning is expected — ignore it locally
- Never run docker compose up without Docker running first
