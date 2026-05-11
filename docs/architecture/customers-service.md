# GPM-48: Customers Service Purpose

## Purpose
Manages all owner and pet data in the PetClinic application.

## Port
8081

## Main business functions
- Create and manage pet owners (name, address, city, telephone)
- Create and manage pets (name, birthdate, type)
- Link pets to their owners
- Retrieve owner and pet information

## Database
MySQL — table: owners, pets, types
In local Docker Compose: H2 in-memory database (resets on restart)
In production (AWS): RDS MySQL (persistent)

## API endpoints (approximate)
- GET /owners — list all owners
- GET /owners/{id} — get owner by ID
- POST /owners — create new owner
- GET /owners/{id}/pets — get pets for owner
- POST /owners/{id}/pets — add pet to owner

## Dependencies
- config-server (configuration)
- discovery-server (service registration)
- MySQL/H2 database

## Spring profile
- Local: default (H2)
- Docker: docker (H2)
- Production: mysql (RDS MySQL)
