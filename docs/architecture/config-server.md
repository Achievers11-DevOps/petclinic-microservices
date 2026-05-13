# GPM-44: Config Server Purpose and Configuration Flow

## Purpose
Centralised configuration management for all microservices.
Every service fetches its configuration from config-server on startup.

## Port
8888

## How it works
1. config-server starts first and loads all configuration files
2. Each service sends a request to config-server on startup:
   http://config-server:8888/{service-name}/{profile}
3. config-server returns the configuration for that service
4. Service uses that configuration to start up

## Configuration profiles
| Profile | Used when |
|---------|-----------|
| default | Local development |
| docker | Running in Docker Compose |
| mysql | Running with MySQL (production) |

## Services that depend on config-server
ALL services — every single service must contact config-server before starting

## Risk
config-server is a single point of failure at startup.
If it is down, no other service can start.

## Production consideration
In production consider running config-server with multiple replicas
or using AWS Parameter Store / Secrets Manager as the config backend.
