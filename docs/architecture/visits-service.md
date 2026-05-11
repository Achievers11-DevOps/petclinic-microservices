# GPM-50: Visits Service Purpose

## Purpose
Manages pet visit records in the PetClinic application.

## Port
8082

## Main business functions
- Record visits made by pets to the clinic
- Store visit date, description, and associated pet
- Retrieve visit history for a pet

## Database
MySQL — table: visits
In local Docker Compose: H2 in-memory database
In production: RDS MySQL

## API endpoints (approximate)
- GET /visits — list all visits
- GET /pets/{petId}/visits — get visit history for a pet
- POST /owners/{ownerId}/pets/{petId}/visits — create new visit

## Dependencies
- config-server (configuration)
- discovery-server (service registration)
- MySQL/H2 database
