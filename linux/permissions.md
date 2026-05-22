# Linux Permissions

Linux permissions control who can read, write, and execute files or directories.

---

# Viewing Permissions

Use:

```bash
ls -l
```

Example output:

```text
-rwxr-xr-- 1 samuel samuel 1024 May 22 script.sh
```

---

# Understanding Permission Structure

Permissions are divided into 3 groups:

```text
rwx | r-x | r--
```

| Group | Meaning |
|---|---|
| First | File owner |
| Second | Group |
| Third | Others |

---

# Permission Meanings

| Symbol | Meaning |
|---|---|
| r | Read |
| w | Write |
| x | Execute |

---

# Numeric Permission System

| Number | Permission |
|---|---|
| 4 | Read |
| 2 | Write |
| 1 | Execute |

Example:



```text
755
```

Results in:

```text
rwxr-xr-x
```

---

# Common Permission Modes

| Mode | Meaning |
|---|---|
| 777 | Full access to everyone |
| 755 | Common for scripts |
| 644 | Common for text files |
| 700 | Private owner access |
| 600 | Sensitive/private files |

---

# Using chmod

Change file permissions:

```bash
chmod 755 script.sh
```

---

# Using chown

Change file ownership:

```bash
sudo chown samuel:samuel script.sh
```

---

# Using sudo

Run commands as administrator:

```bash
sudo apt update
```

---

# Real Lab Practice

Created test files and modified permissions to understand Linux access control.

Commands used:

```bash
touch test.txt
ls -l
chmod 755 test.txt
ls -l
```

---

# What I Learned

- Linux permissions are critical for system security
- Docker containers can fail because of incorrect permissions
- Permissions affect scripts, services, SSH, and mounted volumes
- Understanding chmod and chown is important for infrastructure troubleshooting
