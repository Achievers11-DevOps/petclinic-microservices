# PetClinic Microservices Architecture

## Overview
The PetClinic application is built using a microservices architecture where each service handles a specific responsibility.

## Core Services

### Config Server
Provides centralized configuration management for all microservices.

### Discovery Server
Uses Eureka Service Discovery to register and discover services dynamically.

### API Gateway
Acts as the single entry point for client requests and routes traffic to backend services.

### Customers Service
Handles pet owner and customer information.

### Vets Service
Manages veterinarian information and specialties.

### Visits Service
Stores pet visit and appointment data.

### GenAI Service
Provides AI chatbot integration for PetClinic.

## Monitoring Stack

### Prometheus
Collects application and infrastructure metrics.

### Grafana
Visualizes metrics through dashboards.

## Containerization
Docker was used to containerize all services.

## Orchestration
Kubernetes was used to deploy and manage containers.

## CI/CD
GitHub Actions was used to automate build and test workflows.