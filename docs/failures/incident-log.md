# 🚨 Failure & Debugging Log

## 1. Spring Boot Package Mismatch

Issue:
Unable to find @SpringBootConfiguration

Root Cause:
Incorrect package structure between main and test classes.

Fix:
Standardized package:
com.nomad.springbootdemo

Lesson:
Spring Boot relies heavily on package hierarchy.

---

## 2. Docker Permission Issues in Jenkins

Issue:
docker: Permission denied

Root Cause:
Jenkins container lacked Docker socket access.

Fix:
Mounted /var/run/docker.sock and adjusted permissions.

---

## 3. Kubernetes Rollout Confusion

Issue:
App changes not reflecting in cluster.

Root Cause:
Old Docker image reused.

Fix:
Used versioned tags instead of latest.

---

## 4. Prometheus Metrics Not Found

Issue:
/actuator/prometheus returned 404

Root Cause:
Micrometer endpoint not exposed.

Fix:
Enabled:
management.endpoints.web.exposure.include=prometheus
