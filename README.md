# Prometheus-grafana
# Prometheus and Grafana Monitoring Lab

## Project Overview

This project demonstrates the installation, configuration, and implementation of a monitoring solution using **Prometheus, Grafana, and Node Exporter**.

Prometheus collects and stores metrics, Node Exporter exposes system-level metrics, and Grafana provides dashboards and alerting for monitoring infrastructure.

## Technologies Used

- **Prometheus** – Metrics collection and monitoring
- **Grafana** – Metrics visualization and alerting
- **Node Exporter** – System metrics exporter
- **Docker** – Containerization
- **Docker Compose** – Multi-container management
- **PromQL** – Prometheus Query Language
- **Ubuntu Linux** – Operating system

## Project Structure

```text
prometheus-grafana-lab/
├── compose.yaml
├── prometheus.yml
├── promql-queries.md
├── README.md
└── screenshots/
```

## Tasks Completed

### Task 1: Install Prometheus and Grafana

- Deployed Prometheus and Grafana using Docker Compose.
- Verified that both containers were running.
- Accessed the Prometheus and Grafana web interfaces.

### Task 2: Configure Prometheus

- Configured the Prometheus scrape interval to 15 seconds.
- Added Prometheus and Node Exporter as scrape targets.
- Verified target health through the Prometheus Targets page.

### Task 3: Install and Configure Node Exporter

- Deployed Node Exporter using Docker.
- Exposed metrics on port 9100.
- Verified metrics using the Node Exporter metrics endpoint.
- Integrated Node Exporter with Prometheus.

### Task 4: Execute PromQL Queries

Used PromQL to monitor:

- Target availability
- CPU utilisation
- Memory utilisation
- Filesystem utilisation
- Network traffic

See `promql-queries.md` for the queries and their explanations.

**Note:** Filesystem metrics in this lab reflect the filesystem exposed to the Node Exporter container, not necessarily the complete Ubuntu host filesystem.

### Task 5: Configure Grafana Data Source

- Added Prometheus as a Grafana data source.
- Configured the internal Docker service URL:

`http://prometheus:9090`

- Successfully tested the Prometheus connection.

### Task 6: Create Grafana Dashboard

Created a monitoring dashboard containing:

- CPU Utilisation Gauge
- Memory Utilisation Gauge
- Filesystem Utilisation Gauge
- Network Incoming Traffic Time Series
- Instance selection variable

### Task 7: Configure Alerting

- Created a Grafana alert rule named **High Memory Usage**.
- Configured the memory utilisation PromQL query.
- Set the alert threshold to 50%.
- Configured the evaluation group and interval.
- Created a notification contact point and notification policy.
- Verified that the alert entered the **Firing** state.

Email delivery requires a working SMTP configuration and was not independently verified.

## Access URLs

| Service | URL |
|---|---|
| Prometheus | http://localhost:9090 |
| Prometheus Targets | http://localhost:9090/targets |
| Grafana | http://localhost:3000 |
| Node Exporter | http://localhost:9100/metrics |

## Deployment Instructions

### 1. Clone the repository

```bash
git clone https://github.com/shyamkumarankiaq/Prometheus-grafana.git
cd Prometheus-grafana
```

### 2. Start the monitoring stack

```bash
docker compose up -d
```

### 3. Check running containers

```bash
docker ps
```

### 4. Check Prometheus targets

Open:

http://localhost:9090/targets

Verify that the configured targets are UP.

### 5. Open Grafana

Open:

http://localhost:3000

Log in using your configured Grafana credentials.

## Useful Docker Commands

```bash
# Check running containers
docker ps

# View all containers
docker ps -a

# View Prometheus logs
docker logs prometheus

#
