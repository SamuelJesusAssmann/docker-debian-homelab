# SSH (Secure Shell)

SSH is a protocol used for secure remote access to Linux systems and servers.

It allows:
- remote terminal access
- server administration
- secure communication
- infrastructure management

SSH is widely used in:
- cloud computing
- Linux administration
- DevOps
- infrastructure engineering

---

# Connecting to a Remote Server

Basic SSH connection:

```bash
ssh user@ip-address
```

Example:

```bash
ssh samuel@192.168.0.10
```

---

# SSH Port

Default SSH port:

```text
22
```

Custom ports can also be configured for security purposes.

---

# Checking SSH Service Status

Verify if SSH service is running:

```bash
systemctl status ssh
```

Restart SSH service:

```bash
sudo systemctl restart ssh
```

---

# Installing OpenSSH Server

Install SSH server on Debian/Ubuntu:

```bash
sudo apt install openssh-server
```

Enable service:

```bash
sudo systemctl enable ssh
```

---

# Common SSH Troubleshooting

## Connection Refused

Possible causes:
- SSH service not running
- incorrect IP address
- firewall blocking port 22
- wrong port configuration

---

# Checking Active SSH Connections

View SSH-related processes:

```bash
ps aux | grep ssh
```

---

# SSH Security Basics

Important practices:
- avoid weak passwords
- restrict root login
- use SSH keys when possible
- keep SSH updated

---

# Real Lab Usage

Used SSH to:
- access Debian Server remotely
- manage Docker environment
- execute Linux commands remotely
- troubleshoot infrastructure services

Commands practiced:

```bash
ssh samuel@server-ip
systemctl status ssh
ps aux | grep ssh
```

---

# What I Learned

- SSH is essential for Linux server management
- Most cloud and infrastructure environments use SSH
- Remote administration is a core infrastructure skill
- Troubleshooting SSH involves networking, services, and permissions
- SSH is a foundational technology for DevOps and cloud engineering
