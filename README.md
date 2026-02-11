# nextcloud-cloud-stack
Containerized Nextcloud cloud stack with monitoring, logging and collaboration services

## Overview
This project demonstrates the deployment and operation of a **self-hosted,
production-like Nextcloud cloud platform** with a strong focus on
**DevOps practices**, including containerization, monitoring, logging,
security, and service integration.

All components are deployed as **Docker containers** on a Linux server.
---

## Architecture
The platform consists of multiple interconnected services:

- **Nextcloud (Apache, HTTPS)**
- **PostgreSQL** for persistent data storage
- **Redis** for caching and file locking
- **Prometheus** for metrics collection
- **Nextcloud Exporter** for application-level metrics
- **Grafana** for monitoring dashboards
- **Loki & Promtail** for centralized logging
- **Collabora Online Server** for document collaboration
- **Nextcloud Talk (HPB)** for real-time communication
- **Watchtower** for automated container updates

![Architecture Diagram](docs/architecture.jpg) 
---
## Security & Networking Decisions

- **HTTPS-only access for Nextcloud**  
  Nextcloud is exposed exclusively via port **443** to enforce encrypted access.
  Unencrypted HTTP access is intentionally disabled.

- **Internal-only services**  
  PostgreSQL, Redis, Prometheus, Loki, Promtail and the Nextcloud Exporter are
  only accessible within the Docker network and are not exposed externally.

- **Grafana over HTTP (intentional design choice)**  
  Grafana is exposed via HTTP and intended for internal access only.
  In production environments, TLS termination would typically be handled
  by a reverse proxy or load balancer.

- **Secrets management**  
  Credentials and sensitive values are injected via environment variables
  and are not committed to this repository.
  ---
## Features
- Self-hosted Nextcloud with HTTPS and local domain
- Fully containerized deployment using Docker
- Persistent database backend (PostgreSQL)
- Performance optimization with Redis caching
- Monitoring and observability using Prometheus and Grafana
- Nextcloud-specific metrics via Nextcloud Exporter
- Centralized logging with Loki and Promtail
- Integration of Collabora Online Server
- Automated container updates using Watchtower

---

## Technologies
- Linux (Ubuntu)
- Docker & Docker Compose
- Nextcloud
- PostgreSQL
- Redis
- Prometheus
- Grafana
- Loki & Promtail
- Collabora Online
- HTTPS / TLS

---

## Container Overview
| Service | Docker Image |
|------|-------------|
| Nextcloud | nextcloud:31.x-apache |
| Database | postgres:16 |
| Cache | redis:7 |
| Monitoring | prom/prometheus |
| Metrics Exporter | xperimental/nextcloud-exporter |
| Visualization | grafana/grafana |
| Logging | grafana/loki, grafana/promtail |
| Collaboration | collabora/code |
| Communication | nextcloud/aio-talk |
| Automation | containrrr/watchtower |

---

## Deployment
The stack is deployed using **Docker Compose**.
All services communicate via a shared Docker network.
Configuration is handled through environment variables and
service-specific configuration files.

Sensitive values and secrets are **not included** in this repository.

---

## Monitoring & Observability
- Prometheus collects system and application metrics
- Nextcloud Exporter exposes Nextcloud-specific metrics
- Grafana provides dashboards for monitoring and visualization
- Loki and Promtail enable centralized log aggregation and analysis

---

## Security
- HTTPS/TLS for secure access
- Container isolation between services
- Separation of application, database, and monitoring components
- Restricted network access via Docker networking

---
## Scope & Limitations

This project focuses on a self-hosted, on-premise style deployment.
It does not include public cloud services (AWS, Azure, GCP),
CI/CD pipelines, or infrastructure-as-code tools.

The primary goal is to demonstrate practical DevOps and Cloud fundamentals,
service integration, observability, and secure containerized operations.

---

## Learnings
- Building and operating a containerized cloud platform
- Multi-service orchestration with Docker
- Monitoring and logging in a production-like environment
- Performance optimization using caching
- Integration of collaboration and communication services
- DevOps-oriented operations and maintenance

---

## Project Type
Private hands-on project created to prepare for a
**Junior Cloud / DevOps** role.
