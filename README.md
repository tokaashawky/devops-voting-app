# devops-voting-app
A simple voting application demonstrating Docker-based microservices architecture with a vote service, worker, result service, Redis, PostgreSQL, and a seed service for populating test data.

![Architecture Diagram](./Voting_App/architecture.excalidraw.png)

## Table of Contents
- [Overview](#overview)
- [Setup & Deployment Instructions](#setup--deployment-instructions)
- [Seed Data](#seed-data)
- [Design Decisions & Trade-offs](#design-decisions--trade-offs)
- [Testing & Validation](#testing--validation)

---

## Overview
This project implements a basic voting system with the following services:

- **Vote Service**: Receives votes via HTTP requests.
- **Worker Service**: Processes votes asynchronously.
- **Result Service**: Aggregates and displays vote results.
- **Redis**: Message broker for worker queues.
- **PostgreSQL**: Database storing votes.
- **Seed Service**: Populates the database with sample votes using Apache Bench (`ab`).

All services are containerized using Docker and orchestrated via Docker Compose.

---

## Setup & Deployment Instructions
### 1. Clone the repository
```bash
git clone <your-repo-url>
cd Voting_App
```

### 2. Start core services
Start all primary services except the seed service:
```bash
docker compose up -d 
```
Verify all containers are running and healthy:
```bash
docker ps
```
![Runnig Healthy Containers](./Images/Runnig%20Healthy%20Containers.jpeg)
### 3. Run the seed service
The seed service is optional and runs as a one-time job to populate votes.\
Run using Docker Compose profile:
```bash
docker compose --profile seed up
```
![Result after_seed_before_voting](./Images/Result%20after_seed_before_voting.jpeg)

Note: 
> - Ensure that the vote service is healthy before running the seed service. 
> - The seed service will send 3,000 votes (2,000 for option A, 1,000 for option B) using Apache Bench.

### 4. Access the services
Vote Service: http://localhost:8080 \
Result Service: http://localhost:8081

### 5. Vote and check Result
![Vote after_seed_before_voting](./Images/Vote%20after_seed_before_voting.jpeg)\
![Result after_seed_after_voting](./Images/Result%20after_seed_after_voting.jpeg)
