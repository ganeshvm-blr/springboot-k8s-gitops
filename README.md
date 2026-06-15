# 🚀 Spring Boot CI/CD + Kubernetes + Observability Platform

## 📌 Overview

This project demonstrates a complete end-to-end DevOps system built locally using:

- Spring Boot (Java 17)
- Maven
- Docker
- Jenkins (CI/CD)
- Kubernetes (Minikube)
- Prometheus + Grafana (Observability)

The goal is to simulate a production-grade microservice pipeline:
**Code → Build → Test → Containerize → Deploy → Monitor**

---

## 🏗️ Architecture

Developer
   ↓
GitHub
   ↓
Jenkins CI Pipeline
   ↓
Maven Build (mvnw)
   ↓
Docker Image Build
   ↓
Kubernetes Deployment
   ↓
Prometheus Scraping
   ↓
Grafana Dashboards

---

## 📊 Observability Stack

- Prometheus → Metrics collection
- Grafana → Visualization
- Micrometer → Spring Boot metrics
- Actuator → /actuator/prometheus endpoint

---

## ☸️ Kubernetes Features Used

- Deployments
- Services (ClusterIP + NodePort)
- Ingress (testing phase)
- ServiceMonitor (Prometheus Operator)
- ConfigMaps & YAML-based deployment

---

## ⚙️ CI/CD Pipeline (Jenkins)

Pipeline stages:

1. Git Checkout
2. Maven Build
3. Unit Tests (optional skip)
4. Docker Build
5. Docker Push
6. Kubernetes Deploy

---

## 🚨 Key Engineering Learnings

- Spring Boot package structure directly affects runtime behavior
- Docker containers can run stale images if not rebuilt properly
- Kubernetes does NOT guarantee immediate rollout visibility
- Jenkins failures are mostly environment/tooling issues, not code issues
- Observability must start at application level (Actuator first)

---

## 📂 Documentation

See `/docs` for:

- Architecture decisions
- Failure logs
- Debugging incidents
- Best practices
- ADRs (Architecture Decision Records)

---

## 🧠 Author Insight

This project was built through real debugging cycles across:
- Spring Boot
- Docker
- Jenkins
- Kubernetes

It reflects production-style troubleshooting, not just tutorial execution.
