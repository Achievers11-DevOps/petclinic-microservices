# GPM-39: Local Setup Blockers and Errors

## Blocker 1 — Container Name Conflicts
- Error: container name "/prometheus-server" is already in use
- Cause: previous session containers not cleaned up
- Fix: docker compose down --remove-orphans && docker container prune -f
- Status: Resolved

## Blocker 2 — Services Showing Unhealthy on First Start
- Error: dependency failed to start: container config-server is unhealthy
- Cause: WSL2 is slower than native Linux, health check fires too early
- Fix: run docker compose up -d again after waiting 3 minutes
- Status: Resolved

## Blocker 3 — AZURE_OPENAI_KEY Warning
- Warning: AZURE_OPENAI_KEY variable is not set
- Cause: genai-service uses Azure OpenAI in team repo, key not set locally
- Impact: genai-service AI chat will not work locally — all other services unaffected
- Fix: not required for local testing — expected behaviour
- Status: Known, no action needed

## No Blockers Found
- Java 17: available via WSL2
- Docker: running correctly
- Docker Compose v2: working
- All ports available with no conflicts
- All 11 services started successfully
