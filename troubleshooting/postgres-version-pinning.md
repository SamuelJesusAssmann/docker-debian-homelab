# PostgreSQL Version Pinning

## Issue

PostgreSQL container entered a restart loop after VM reboot.

## Symptoms

- Container continuously restarting
- PostgreSQL unavailable
- Docker logs displaying storage compatibility errors

## Root Cause

The container was configured using:

```yaml
image: postgres:latest
```

After restart, Docker pulled a newer PostgreSQL version automatically.

The existing database volume was incompatible with the new internal storage format.

## Solution

Pinned the PostgreSQL image version:

```yaml
image: postgres:16
```

## Lessons Learned

- Avoid using `latest` tags for stateful services
- Database containers should use fixed versions
- Volume compatibility must be considered during upgrades
- Infrastructure should be predictable across reboots
