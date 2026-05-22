# PostgreSQL Volume Conflict

## Problem
PostgreSQL container entered restart loop after changing image version and volume mappings.

## Error
initdb: error: directory "/var/lib/postgresql/data" exists but is not empty

## Cause
Old database files remained inside the mounted Docker volume.

## Solution
docker compose down
sudo rm -rf ../volumes/postgres/*
docker compose up -d

## Result
PostgreSQL container started successfully and accepted connections.
