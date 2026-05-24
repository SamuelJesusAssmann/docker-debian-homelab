# SupportFlow Containerization and Deployment

## Objective

Create, containerize and deploy the SupportFlow API inside the Debian Docker homelab environment.

---

# Environment

- Debian Server
- Docker
- Docker Compose
- FastAPI
- VSCode Remote SSH
- Uptime Kuma

---

# Project Structure

```text
supportflow/
├── app/
│   └── main.py
├── Dockerfile
├── docker-compose.yml
└── requirements.txt
```

---

# Step 1 — Creating the project directory

Create the project structure:

```bash
mkdir -p ~/docker/supportflow/app
```

Navigate to the project directory:

```bash
cd ~/docker/supportflow
```

---

# Step 2 — Creating the API

File created:

```text
app/main.py
```

Features implemented:
- Healthcheck endpoint
- Ticket creation
- Ticket listing
- Ticket retrieval by ID

Main endpoints:

```text
GET /
GET /status
POST /tickets
GET /tickets
GET /tickets/{ticket_id}
```

---

# Step 3 — Creating requirements.txt

File:

```text
requirements.txt
```

Content:

```txt
fastapi
uvicorn
pydantic
```

Purpose:
- Install FastAPI
- Install ASGI server (Uvicorn)
- Install data validation library (Pydantic)

---

# Step 4 — Creating the Dockerfile

File:

```text
Dockerfile
```

Content:

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Purpose:
- Create Python environment
- Install dependencies
- Copy application files
- Start FastAPI inside the container

---

# Step 5 — Creating docker-compose.yml

File:

```text
docker-compose.yml
```

Content:

```yaml
services:
  supportflow:
    build: .
    container_name: supportflow
    ports:
      - "8001:8000"
    restart: unless-stopped
```

Purpose:
- Build the container
- Expose API port
- Keep service persistent

---

# Step 6 — Building and starting the container

Build and start the application:

```bash
docker compose up -d --build
```

Verify running containers:

```bash
docker ps
```

Expected result:

```text
supportflow   Up
```

---

# Step 7 — Testing the API

Swagger documentation:

```text
http://SERVER-IP:8001/docs
```

Healthcheck endpoint:

```text
http://SERVER-IP:8001/status
```

---

# Step 8 — Monitoring with Uptime Kuma

Monitor created:
- Type: HTTP(s)
- Endpoint: `/status`
- Interval: 60 seconds
- Tag: Backend

Metrics monitored:
- Uptime
- Response time
- Heartbeat history
- Availability

---

# Monitoring Test

Simulating downtime:

```bash
docker stop supportflow
```

Expected behavior:
- Uptime Kuma detects downtime
- Monitor turns red
- Service marked as unavailable

Recovering service:

```bash
docker start supportflow
```

Expected behavior:
- Service returns online
- Monitor turns green again

---

# Skills Practiced

- FastAPI development
- Docker containerization
- Docker Compose orchestration
- Linux server management
- VSCode Remote SSH
- API deployment
- Infrastructure monitoring
- Observability
- Troubleshooting

---

# Screenshots

Directory:

```text
screenshots/supportflow/
```


---

# Final Result

SupportFlow API successfully deployed and monitored inside a Debian Docker homelab environment.

The environment now includes:
- Containerized backend API
- Infrastructure monitoring
- Docker-based deployment workflow
- Service observability
- Remote Linux development environment
