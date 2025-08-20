# Docker Database Services Boilerplate

This repository provides a ready-to-use Docker Compose setup for common database and monitoring needs. It bundles persistent PostgreSQL and Redis services, automated backups via SQLBak, and a full Prometheus monitoring stack with cAdvisor and exporters. Use it as a starting point for local development or small deployments.

## Services
- **PostgreSQL** – Primary relational database with persistent volume and credentials supplied through environment variables.
- **Redis** – In-memory key‑value store configured with password protection and persistent volume.
- **SQLBak** – Automated backup service that uploads database dumps to external storage using your SQLBak account key.
- **Prometheus** – Monitoring server that scrapes metrics from exporters and stores them on a dedicated volume.
- **PostgreSQL Exporter** and **Redis Exporter** – Expose database metrics for Prometheus.
- **Node Exporter** – Collects host machine metrics.
- **cAdvisor** – Container resource monitoring, also scraped by Prometheus.

## Getting Started
1. Copy the example environment file and adjust credentials:
   ```bash
   cp .env.example .env
   # Edit .env with your preferred usernames, passwords and SQLBak token
   ```
   If you don't have a SQLBak token yet, sign up for a free account at [https://sqlbak.com](https://sqlbak.com)
   to generate one.
2. Launch the stack:
   ```bash
   docker compose up -d
   ```
3. Access services:
   - PostgreSQL: `localhost:5432`
   - Redis: `localhost:6379`
   - Prometheus UI: [http://localhost:9090](http://localhost:9090)
   - cAdvisor UI: [http://localhost:8080](http://localhost:8080)

## Additional Docs
- [`restore_db.md`](restore_db.md) – Notes for restoring databases.
- [`tunning_db.md`](tunning_db.md) – Tips for performance tuning.
- [`prometheus/`](prometheus/) – Custom Prometheus configuration.

## License
This project is released under the MIT License.
