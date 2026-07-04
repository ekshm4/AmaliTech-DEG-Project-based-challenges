# Deployment Guide - Kora Analytics API

## Cloud Provider
**AWS EC2** (t2.micro, free tier) running Ubuntu 22.04 LTS.

Chosen for free tier eligibility and industry standard cloud platform.

## VM Setup
1. Launched EC2 t2.micro with Ubuntu 22.04 LTS AMI
2. Security group rules:
   - HTTP (port 80) from 0.0.0.0/0
   - SSH (port 22) from my IP only
3. Downloaded and configured kora-key.pem

## Docker Installation
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker ubuntu
```

Reconnect SSH session for group changes to take effect.

## Checking the Container
```bash
docker ps
```

Shows the `kora-api` container running from the Docker Hub image.

## Viewing Logs
```bash
docker logs kora-api
```

Output: `Server running on port 3000`

## Live Endpoint
```
GET http://<ec2-ip>/health
{"status":"ok"}
```
