# Linux Services & systemctl

systemctl is used to manage Linux services in systems using systemd.

Services are background processes responsible for running important system components such as:
- Docker
- SSH
- databases
- web servers
- networking tools

---

# Checking Service Status

Check if a service is running:

```bash
systemctl status docker
```

Example output:
- active (running)
- inactive
- failed

---

# Starting Services

Start a service manually:

```bash
sudo systemctl start docker
```

---

# Stopping Services

Stop a running service:

```bash
sudo systemctl stop docker
```

---

# Restarting Services

Restart a service:

```bash
sudo systemctl restart docker
```

Useful after:
- configuration changes
- updates
- troubleshooting

---

# Enabling Services on Boot

Start service automatically during system boot:

```bash
sudo systemctl enable docker
```

---

# Disabling Services

Prevent service from starting automatically:

```bash
sudo systemctl disable docker
```

---

# Viewing Failed Services

Check failed services:

```bash
systemctl --failed
```

---

# Viewing Logs with journalctl

View logs from a service:

```bash
journalctl -u docker
```

Follow logs in real time:

```bash
journalctl -u docker -f
```

---

# Real Lab Usage

Used systemctl to:
- verify Docker service status
- restart Docker during troubleshooting
- confirm services were active after boot
- diagnose startup issues

Commands used:

```bash
systemctl status docker
sudo systemctl restart docker
journalctl -u docker
```

---

# What I Learned

- Linux services run important infrastructure components
- systemctl is essential for troubleshooting servers
- Many issues can be diagnosed by checking service status and logs
- Docker, SSH, and databases are managed as services
- Restarting services is common during infrastructure maintenance
