# GPM-49: Vets Service Purpose

## Purpose
Manages veterinarian data in the PetClinic application.

## Port
8083

## Main business functions
- Store and retrieve veterinarian information
- Manage vet specialities (surgery, dentistry, radiology)
- Provide vet listing for the application UI

## Database
MySQL — table: vets, specialities, vet_specialities
Local: H2 in-memory
Production: RDS MySQL

## API endpoints
- GET /vets — list all vets with their specialities

## Dependencies
- config-server
- discovery-server
- MySQL/H2 database
