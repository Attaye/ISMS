IT-Security Dashboard (ISMS)

The IT-Security Dashboard is a modular microservice-based platform designed to support companies in managing information security according to ISMS principles (e.g., ISO 27001, BSI Grundschutz).
It provides centralized visibility, risk assessment, and audit-ready documentation through a modern, containerized backend architecture.

Features:
- User Management – Role-based access control (Admin, Auditor, User) with JWT authentication
- Asset Management – Register and track IT systems, devices, and applications
- Vulnerability Management – Identify, analyze, and evaluate risks (CVSS support)
- Risk Mitigation – Track and manage measures to minimize security risks
- Audit & Reports – Generate PDF reports for audits and external stakeholders
- Audit Logging – Complete audit trail of all relevant security changes

Architecture:
- Microservices (Spring Boot + PostgreSQL)
  - auth-service – Authentication, JWT, RBAC
  - asset-service – IT asset management
  - vulnerability-service – Vulnerability tracking & risk scoring
  - mitigation-service – Risk treatment & action plans
  - report-service – PDF exports & report aggregation
  - log-service – Centralized audit trail
- API Gateway: KrakenD
  - Aggregates & routes REST endpoints
  - JWT validation & authentication
  - Optional caching & load balancing
- Deployment: Docker Compose for local setup, prepared for Kubernetes/K3s & cloud (AWS/GCP).

Tech Stack:
- Backend: Java 21, Spring Boot, Spring Security, Spring Data JPA
- Database: PostgreSQL + Liquibase migrations
- API Gateway: KrakenD
- Containerization: Docker, Docker Compose
- Observability (planned): OpenTelemetry, Prometheus, Grafana

Roadmap:
- Risk & Compliance Service (risk register, frameworks, controls)
- Document & Policy Service (policy lifecycle, storage)
- Threat Intelligence & Search Service (Elasticsearch, CVE feeds)
- Advanced security hardening (SSO, mTLS, OPA, PITR backups)

License:
This project is developed as part of an educational & professional portfolio.