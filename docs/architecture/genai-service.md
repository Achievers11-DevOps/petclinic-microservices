# GPM-51: GenAI Service Purpose

## Purpose
AI-powered chat assistant for the PetClinic application.
Allows users to ask questions about their pets and get AI responses.

## Port
8084

## Main business functions
- Accept natural language questions from users
- Send questions to OpenAI/Azure OpenAI API
- Return AI-generated responses to the UI
- Provides a chat interface within the PetClinic app

## Dependencies
- config-server (configuration)
- discovery-server (service registration)
- OpenAI API key (OPENAI_API_KEY or AZURE_OPENAI_KEY)
- Azure OpenAI endpoint (AZURE_OPENAI_ENDPOINT) in team repo

## Local behaviour
- AZURE_OPENAI_KEY and AZURE_OPENAI_ENDPOINT not set locally
- Service starts but AI chat will not work without the keys
- Warning messages in logs are expected — not an error

## Production setup
- API key stored in AWS Secrets Manager
- Synced to Kubernetes via External Secrets Operator
- Mounted as environment variable in the pod

## Model used
- Team repo: Azure OpenAI (gpt-4o or similar)
- Project B solo: OpenAI gpt-4o-mini
