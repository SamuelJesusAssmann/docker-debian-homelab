# Linux Troubleshooting

Troubleshooting is the process of identifying, diagnosing, and resolving technical problems in Linux systems and infrastructure environments.

It is one of the most important skills in:
- technical support
- infrastructure engineering
- cloud operations
- DevOps
- system administration

---

# Troubleshooting Mindset

Instead of asking:

```text
"Why is everything broken?"
```

A better approach is:

```text
"Where in the system flow did the failure happen?"
```

---

# Common Troubleshooting Areas

- services
- networking
- permissions
- processes
- Docker containers
- SSH access
- ports
- logs
- resource usage

---

# Basic Troubleshooting Workflow

## 1. Identify the problem
Examples:
- service not starting
- SSH connection refused
- container crash
- network unavailable

---

## 2. Check service status

```bash
systemctl status docker
```

---

## 3. Inspect logs

```bash
journalctl -u docker
```

or:

```bash
tail -f /var/log/syslog
```

---

## 4. Verify processes

```bash
ps aux
```

or:

```bash
top
```

---

## 5. Check networking

Examples:
- verify IP address
- test connectivity
- inspect open ports

Commands:

```bash
ping google.com
ip a
ss -tulnp
```

---

## 6. Verify permissions

Example:

```bash
ls -l
chmod
chown
```

---

# Docker Troubleshooting Example

## Problem
Redis container failed to start.

## Investigation
- checked container logs
- inspected ports
- verified running services

Commands used:

```bash
docker ps
docker logs
ss -tulnp
```

## Cause
Port conflict on 6379.

## Solution
Stopped conflicting service and restarted Docker Compose.

---

# SSH Troubleshooting Example

## Problem
SSH connection refused.

## Investigation
- verified SSH service status
- checked network connectivity
- inspected firewall/port configuration

Commands used:

```bash
systemctl status ssh
ping
ss -tulnp
```

---

# Important Troubleshooting Tools

| Tool | Purpose |
|---|---|
| systemctl | service management |
| journalctl | logs |
| ps aux | process inspection |
| top / htop | monitoring |
| ping | connectivity testing |
| ss -tulnp | open ports |
| ls -l | permissions |
| docker logs | container debugging |

---

# What I Learned

- Troubleshooting is a systematic investigation process
- Logs are critical for diagnosing failures
- Many infrastructure issues involve services, networking, or permissions
- Understanding system flow improves problem-solving
- Troubleshooting skills are essential for support engineering and infrastructure roles
