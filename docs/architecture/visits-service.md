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
Local: H2 in-memory
Production: RDS MySQL

## API endpoints
- GET /visits — list all visits
- GET /pets/{petId}/visits — get visit history for a pet
- POST /owners/{ownerId}/pets/{petId}/visits — create new visit

## Dependencies
- config-server
- discovery-server
- MySQL/H2 database
