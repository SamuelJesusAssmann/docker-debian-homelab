# Redis Port Conflict

## Problem
Docker container failed to start because port 6379 was already in use.

## Symptoms
- Redis container stopped immediately
- Docker Compose returned port binding errors
- Services depending on Redis failed to start

## Cause
Another Redis instance was already running on the server and occupying port 6379.

## Troubleshooting Steps

### Check active containers
```bash
docker ps
```

### Check processes using port 6379
```bash
sudo lsof -i :6379
```

### Stop conflicting container/service
```bash
docker stop <container_id>
```

## Solution
Removed the conflicting Redis instance and restarted Docker Compose successfully.

```bash
docker compose up -d
```

## Lessons Learned
- Always verify used ports before deploying containers
- Use container naming standards
- Document infrastructure conflicts for future troubleshooting
