# Linux Processes

Processes are running programs and services inside the Linux operating system.

Monitoring processes is essential for:
- troubleshooting
- performance analysis
- infrastructure management
- server administration

---

# Listing Processes

View running processes:

```bash
ps aux
```

Useful information:
- USER
- PID
- CPU usage
- memory usage
- command name

---

# Real-Time Process Monitoring

Monitor processes in real time:

```bash
top
```

Useful for:
- CPU monitoring
- memory usage
- identifying high resource consumption

---

# htop

Improved interactive process viewer:

```bash
htop
```

Features:
- easier navigation
- colored interface
- process filtering
- process management

Install:

```bash
sudo apt install htop
```

---

# Killing Processes

Terminate a process using PID:

```bash
kill 1234
```

Force kill:

```bash
kill -9 1234
```

---

# killall

Kill processes by name:

```bash
killall firefox
```

Useful when:
- multiple instances exist
- process names are known

---

# Finding Process IDs

Find process by name:

```bash
ps aux | grep docker
```

Example:
- identify Docker daemon
- locate running services
- troubleshoot stuck applications

---

# Real Lab Usage

Used process management commands to:
- inspect running Docker services
- monitor Linux resource usage
- identify active processes
- troubleshoot stuck services
- verify infrastructure components

Commands practiced:

```bash
ps aux
top
htop
ps aux | grep docker
```

---

# What I Learned

- Linux runs many background processes simultaneously
- Process monitoring is critical for troubleshooting
- top and htop help identify resource issues
- kill and killall can stop problematic applications
- Process management is important for infrastructure and server administration
