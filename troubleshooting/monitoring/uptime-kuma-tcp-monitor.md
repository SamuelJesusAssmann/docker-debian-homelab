# Uptime Kuma TCP Monitor Configuration

## Overview

This document describes the configuration and troubleshooting process used to monitor Redis using Uptime Kuma in a Debian Docker homelab environment.

---

## Environment

- Debian Server
- Docker Compose
- Redis Container
- Uptime Kuma
- Portainer

---

## Initial Problem

Redis container was operational and running correctly, but Uptime Kuma reported the service as OFFLINE.

### Symptoms

- Redis container visible in `docker ps`
- Redis accessible internally
- Uptime Kuma status showing:
  - OFFLINE
  - 0% uptime
  - No valid response data

---

## Root Cause

The monitor was incorrectly configured using:

- Monitor Type: HTTP(s)

Redis does not provide HTTP responses on port `6379`.

Because of this, the monitor continuously failed despite the service being healthy.

---

## Verification Commands

### Check container status

```bash
docker ps
```

### Verify Redis port exposure

```bash
ss -tulpn | grep 6379
```

### Inspect logs

```bash
docker logs redis
```

---

## Solution

The monitor type was changed from:

```txt
HTTP(s)
```

to:

```txt
TCP Port
```

---

## Correct Monitor Configuration

### General

| Setting | Value |
|---|---|
| Monitor Type | TCP Port |
| Friendly Name | Docker - Redis |
| Host | 172.18.13.159 |
| Port | 6379 |
| Heartbeat Interval | 20 seconds |

---

## Result

After reconfiguration:

- Redis status changed to ONLINE
- Uptime monitoring recovered
- Ping values became visible
- Historical downtime remained recorded

---

## Additional Notes

### False Positive Monitoring

This issue demonstrated how incorrect monitoring protocols can generate false outage alerts even when services are functioning normally.

### Lesson Learned

Different services require different monitoring methods:

| Service Type | Recommended Monitor |
|---|---|
| Web Applications | HTTP(s) |
| Redis | TCP Port |
| Databases | TCP Port |
| APIs | HTTP(s) |

---

## Related Services

Current homelab services:

- PostgreSQL
- Redis
- Portainer
- Uptime Kuma

---

## Infrastructure Stack

- Debian Linux
- Docker
- Docker Compose
- Uptime Kuma
- Portainer

---

## Status Page

A public status page was also configured for infrastructure visibility and incident tracking.

Example incident created during testing:

```txt
Redis service instability detected after container restart.
```

---

## Lessons Learned

- Validate monitoring protocol compatibility
- Redis should be monitored through TCP checks
- Monitoring failures do not always indicate service failures
- Historical uptime graphs help identify configuration issues
- Incident documentation improves troubleshooting workflows
