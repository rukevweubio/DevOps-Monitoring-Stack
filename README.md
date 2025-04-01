# DevOps-Monitoring-Stack# DevOps Monitoring Stack

## Overview

This project provides a comprehensive monitoring and observability stack for a containerized environment using **Docker Swarm** for orchestration. The stack includes **Nginx**, **PostgreSQL**, **Prometheus**, **Grafana**, **Loki**, and **Promtail** to monitor and visualize the health, performance, and logs of the system. 

The primary focus is on monitoring the **Nginx reverse proxy** and the **PostgreSQL database**, ensuring that logs and metrics are collected, stored, and visualized effectively.

---

## Problem Statement

In modern containerized environments, managing and monitoring the health and performance of services is critical. Without proper observability, it becomes challenging to:

1. Detect and troubleshoot issues in real-time.
2. Analyze logs and metrics to identify performance bottlenecks.
3. Ensure the reliability and availability of critical services like Nginx and PostgreSQL.

Specifically, this project addresses the following challenges:
- Lack of centralized logging for Nginx and PostgreSQL.
- Difficulty in visualizing metrics and logs for troubleshooting.
- Absence of a scalable solution for monitoring containerized services in a Docker Swarm environment.

---

## Solution

This project implements a **DevOps Monitoring Stack** to solve the above challenges by integrating the following tools:

### 1. **Nginx**
   - Acts as a reverse proxy for incoming HTTP traffic.
   - Logs are collected and monitored for error detection and traffic analysis.

### 2. **PostgreSQL**
   - A relational database used for application data storage.
   - Metrics and logs are monitored to ensure database health and performance.

### 3. **Prometheus**
   - Collects metrics from services like PostgreSQL and cAdvisor.
   - Provides a time-series database for storing metrics.

### 4. **Grafana**
   - Visualizes metrics and logs in customizable dashboards.
   - Enables real-time monitoring and alerting.

### 5. **Loki**
   - Centralized log aggregation system.
   - Stores logs from Nginx and PostgreSQL for analysis.

### 6. **Promtail**
   - Collects logs from Nginx and PostgreSQL.
   - Pushes logs to Loki for centralized storage.

### 7. **Docker Swarm**
   - Orchestrates the deployment of all services.
   - Ensures scalability and fault tolerance.

---

## Architecture

The stack is deployed using **Docker Swarm** and consists of the following components:

1. **Nginx**: Serves as a reverse proxy and generates access and error logs.
2. **PostgreSQL**: Stores application data and exposes metrics via the PostgreSQL Exporter.
3. **Prometheus**: Scrapes metrics from PostgreSQL, cAdvisor, and itself.
4. **Grafana**: Provides dashboards for visualizing metrics and logs.
5. **Loki**: Aggregates logs from Nginx and PostgreSQL.
6. **Promtail**: Collects logs and forwards them to Loki.
7. **cAdvisor**: Monitors container resource usage.

---

## Deployment

### Prerequisites
- Docker and Docker Swarm installed on the host machine.
- Basic knowledge of Docker Swarm orchestration.

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/rukevweubio/DevOps-Monitoring-Stack
   cd DevOps-Monitoring-Stack
   ```

   initailize the docker swarm 
   ```docker swarm init
   ```
   deploy the docker-compose file 
   ```
   docker stack deploy -c docker-compose.yaml monitoring-stack
   ```
Monitoring Details
Logs
- Nginx Logs: Collected by Promtail and stored in Loki.
- PostgreSQL Logs: Collected by Promtail and stored in Loki.
Metrics
- Nginx Metrics: Monitored via Prometheus.
- PostgreSQL Metrics: Exported via PostgreSQL Exporter and scraped by Prometheus.
- Container Metrics: Monitored via cAdvisor.

### Customization
- Modify promtail-config.yaml to add or update log sources.
- Update prometheus.yml to scrape additional metrics.
- Customize Grafana dashboards to suit your monitoring needs.

#### Conclusion
This monitoring stack provides a robust solution for observing and troubleshooting containerized environments. By integrating Nginx, PostgreSQL, Prometheus, Grafana, Loki, and Promtail, it ensures centralized logging and metrics visualization, 
