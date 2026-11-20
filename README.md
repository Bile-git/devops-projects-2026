# DevOps Projects 2026

A hands-on portfolio of infrastructure, containerization, Linux operations, CI/CD, monitoring, and Kubernetes learning projects.

This repository brings related implementation work and technical design documentation together so that each project can be reviewed independently.

## Projects

### 1. Containerized AI Chatbot

**Path:** [chatbot-app-docker](./chatbot-app-docker)

A multi-container application environment with configuration for:

- FastAPI backend and frontend application
- PostgreSQL database with persistent storage
- Docker Compose networking and service dependencies
- Prometheus metrics collection and Grafana dashboards
- Dockerfiles and Jenkins pipeline files for the application components

**Useful files**
- [Docker Compose configuration](./chatbot-app-docker/compose.yaml)
- [Containerization guide](./chatbot-app-docker/containerization_guide.md)
- [Architecture diagram](./chatbot-app-docker/docker-project-architecture.png)

**Run locally**

From the project directory:

```bash
cd chatbot-app-docker
```

Review the Compose file and backend environment sample first. Configure required API credentials and database settings using local environment files that are not committed to Git. Then start the services:

```bash
docker compose config
docker compose up --build -d
docker compose ps
```

The Compose configuration maps the frontend to port 3000, the backend to 8000, Prometheus to 9090, and Grafana to 3001. Confirm the actual service health and application endpoints in your environment before relying on them.

### 2. Linux Multi-VM Application Architecture

**Path:** [chatbot-app-linux](./chatbot-app-linux)

Design and deployment documentation for a multi-tier Linux-hosted AI question-answering application. The architecture separates responsibilities across five virtual machines:

1. Nginx reverse proxy
2. Node.js frontend
3. FastAPI backend
4. PostgreSQL database
5. Prometheus and Grafana monitoring

**Documentation**
- [Architecture and network design](./chatbot-app-linux/architecture.md)
- [Installation guide](./chatbot-app-linux/installation_guide.md)
- [Server guide](./chatbot-app-linux/server_guide.md)
- [Backend guide](./chatbot-app-linux/backend_guide.md)
- [Monitoring guide](./chatbot-app-linux/monitoring_guide.md)
- [Architecture diagram](./chatbot-app-linux/diagram-chatbot-linux.png)

The architecture document describes the target design. Review the individual guides and deployment evidence to distinguish completed implementation steps from planned or optional components.

### 3. RAG Application on Kubernetes

**Path:** [rag-app-kubernetes](./rag-app-kubernetes)

Infrastructure planning and architecture material for deploying a retrieval-augmented generation application on Kubernetes. The documented environment covers:

- Jenkins for CI automation
- Kubernetes for workload orchestration
- MetalLB for LoadBalancer IP allocation
- Application services for ingestion and querying
- Qdrant vector database integration
- Argo CD as an optional GitOps component

**Documentation and diagrams**
- [Infrastructure requirements](./rag-app-kubernetes/infrastructure.md)
- [Kubernetes architecture diagram](./rag-app-kubernetes/k8s-ai-project.png)
- [RAG workflow diagram](./rag-app-kubernetes/rag-diagram.png)

The infrastructure document is a requirements and design guide; it should not be read as proof that every listed component is currently deployed.

## Technology Areas

| Area | Technologies represented in this repository |
|---|---|
| Containers | Docker, Docker Compose |
| CI/CD | Jenkins pipeline files |
| Linux and web | Linux, Nginx, Node.js |
| Backend and data | Python, FastAPI, PostgreSQL |
| Orchestration | Kubernetes |
| Monitoring | Prometheus, Grafana |
| RAG infrastructure | Qdrant, MetalLB, Argo CD (optional) |

## Repository Structure

```text
devops-projects-2026/
├── chatbot-app-docker/
│   ├── backend/
│   ├── frontend/
│   ├── prometheus/
│   ├── compose.yaml
│   └── containerization_guide.md
├── chatbot-app-linux/
│   ├── architecture.md
│   ├── installation_guide.md
│   ├── server_guide.md
│   ├── backend_guide.md
│   └── monitoring_guide.md
└── rag-app-kubernetes/
    └── infrastructure.md
```

## Safe Configuration

- Do not commit API keys, passwords, private keys, cloud credentials, or populated environment files.
- Use local `.env` files or a secrets manager for sensitive configuration.
- Keep `.env` files out of Git and provide sanitized `.env.example` files for setup.
- Use version-pinned container images for reproducible environments rather than relying on `:latest` in production.
- Restrict database and monitoring ports to trusted networks when deploying beyond a local lab.

## Validation Checklist

Before describing a project as deployed or production-ready, record evidence for the relevant items:

- [ ] Build completes successfully.
- [ ] Containers or services start and pass health checks.
- [ ] Application endpoints respond as expected.
- [ ] Database persistence works after a restart.
- [ ] Prometheus scrapes the intended targets and Grafana dashboards display metrics.
- [ ] Jenkins pipeline completes successfully.
- [ ] Kubernetes workloads become Ready and services are reachable.
- [ ] Setup steps have been tested from a clean environment.

## About This Portfolio

These projects are intended to demonstrate practical learning and hands-on work with cloud-native and DevOps tools. Individual project documentation identifies architecture, configuration, and setup guidance; implementation status should be described accurately based on tests and deployment evidence.

---

**Maintainer:** [Bile-git](https://github.com/Bile-git)
