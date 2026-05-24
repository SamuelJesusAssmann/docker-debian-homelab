![Docker](https://img.shields.io/badge/Docker-Enabled-blue)
![Debian](https://img.shields.io/badge/OS-Debian-red)
![Status](https://img.shields.io/badge/Status-Active-green)
![DevOps](https://img.shields.io/badge/Focus-DevOps-purple)
# Aura Systems - Docker Debian Homelab

Personal infrastructure and containerization lab built on Debian Server using Docker technologies.

This project documents my journey learning Linux administration, Docker, monitoring, networking, troubleshooting, and self-hosted infrastructure.

---

## Infrastructure Stack

### Operating System
- Debian Server

### Containerization
- Docker
- Docker Compose

### Services
- Redis
- PostgreSQL
- Portainer
- Uptime Kuma

### Development Tools
- VSCode Remote SSH

---

## Current Features

- Containerized infrastructure
- Service monitoring with Uptime Kuma
- Custom status page
- Redis TCP monitoring
- Remote development environment
- Docker Compose orchestration
- Infrastructure troubleshooting documentation
- Service uptime tracking

---

## Learning Goals

This homelab was created to improve practical skills in:

- Linux administration
- Docker ecosystem
- Container networking
- Monitoring and observability
- Troubleshooting
- Infrastructure documentation
- Self-hosted environments
- DevOps fundamentals

---

## What I Practiced

### Linux
- File system navigation
- SSH access
- Service management
- Terminal workflow
- Logs analysis

### Docker
- Container lifecycle management
- Docker Compose workflows
- Port mapping
- Persistent volumes
- Network troubleshooting

### Monitoring
- Uptime Kuma setup
- TCP service monitoring
- Incident simulation
- Status page customization

### Infrastructure
- Remote development using VSCode SSH
- Multi-container environments
- Infrastructure organization
- Documentation practices

---

## Troubleshooting Examples

### Redis monitoring failure

#### Issue
Redis container was running correctly but Uptime Kuma reported the service as offline.

#### Root Cause
The monitor was configured incorrectly using HTTP instead of TCP monitoring.

#### Solution
- Reconfigured the monitor to use TCP mode
- Validated Redis port accessibility
- Confirmed uptime recovery through Kuma

---

### PostgreSQL restart loop

#### Issue
PostgreSQL entered a restart loop after VM reboot.

#### Investigation
Container logs showed PostgreSQL version and collation mismatch warnings.

#### Actions Taken
- Inspected container logs
- Validated persistent volumes
- Tested container recreation workflow
- Documented recurring behavior for future fixes

---

## Current Repository Structure

```bash
docker-debian-homelab/
├── linux/
├── troubleshooting/
├── screenshots/
└── README.md
