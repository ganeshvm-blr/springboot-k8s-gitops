# 🏗️ System Architecture

## Flow

GitHub → Jenkins → Maven → Docker → Kubernetes → Prometheus → Grafana

## Components

- Spring Boot: REST API + Actuator
- Jenkins: CI/CD automation
- Docker: Containerization
- Kubernetes: Orchestration
- Prometheus: Metrics scraping
- Grafana: Visualization

## Key Design Decisions

- Used Maven Wrapper for portability
- Used ClusterIP for internal services
- Used NodePort for local testing
- Used Micrometer for metrics standardization

