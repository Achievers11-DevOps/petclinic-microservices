# GPM-49: Vets Service Purpose

## Purpose
Manages veterinarian data in the PetClinic application.

## Port
8083

## Main business functions
- Store and retrieve veterinarian information
- Manage vet specialities (surgery, dentistry, radiology etc.)
- Provide vet listing for the application UI

## Database
MySQL — table: vets, specialities, vet_specialities
In local Docker Compose: H2 in-memory database
In production: RDS MySQL

## API endpoints (approximate)
- GET /vets — list all vets with their specialities

## Dependencies
- config-server (configuration)
- discovery-server (service registration)
- MySQL/H2 database

## Notes
Vets data is relatively static — does not change often.
Good candidate for caching in a production optimisation.
