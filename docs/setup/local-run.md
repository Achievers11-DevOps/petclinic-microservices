# GPM-38: Run the Application Locally — Greg's Evidence

## Machine
WSL2 Ubuntu on Windows — greg@DESKTOP-80FBOLN

## Commands Run
sudo service docker start
docker compose down --remove-orphans
docker container prune -f
docker compose up -d

## Result — All 11 Containers Running on Greg's Machine
| Container | Status | Port |
|-----------|--------|------|
| config-server | Healthy | 8888 |
| discovery-server | Healthy | 8761 |
| api-gateway | Up | 8080 |
| customers-service | Up | 8081 |
| vets-service | Up | 8083 |
| visits-service | Up | 8082 |
| admin-server | Up | 9090 |
| genai-service | Up | 8084 |
| grafana-server | Up | 3030 |
| prometheus-server | Up | 9091 |
| tracing-server | Up | 9411 |

## URLs Verified in Browser by Greg
| URL | Service | Status |
|-----|---------|--------|
| http://localhost:8080 | PetClinic App | Accessible |
| http://localhost:8761 | Eureka Dashboard | Accessible |
| http://localhost:9090 | Admin Server | Accessible |
| http://localhost:3030 | Grafana | Accessible |
| http://localhost:9091 | Prometheus | Accessible |
| http://localhost:9411 | Zipkin | Accessible |

## Known Behaviour
- Owners page shows empty — H2 in-memory database starts empty locally
- This is expected — production uses RDS MySQL with persistent data
- AZURE_OPENAI_KEY warning is expected — genai-service runs without AI locally
