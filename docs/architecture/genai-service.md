# GPM-51: GenAI Service Purpose

## Purpose
AI-powered chat assistant for the PetClinic application.

## Port
8084

## Main business functions
- Accept natural language questions from users
- Send questions to Azure OpenAI API
- Return AI-generated responses to the UI

## Dependencies
- config-server
- discovery-server
- AZURE_OPENAI_KEY environment variable
- AZURE_OPENAI_ENDPOINT environment variable

## Local behaviour
- Warnings about missing keys are expected — not an error
- Service starts but AI chat will not work without keys
- All other services are unaffected

## Production setup
- API key stored in AWS Secrets Manager
- Synced to Kubernetes via External Secrets Operator
- Mounted as environment variable in the pod
