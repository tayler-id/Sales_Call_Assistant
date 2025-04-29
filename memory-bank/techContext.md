# Technical Context

This document details the technologies used, development setup, technical constraints, dependencies, and tool usage patterns.

## Technologies Used

- Kubernetes with GPU and CPU node groups
- Docker with distroless base images
- Kafka for event streaming
- gRPC for service communication
- Whisper-T GPU pods for speech-to-text
- GPT-5 / Claude-Next for NLP orchestration
- Redis for caching
- React + Vite for frontend UI
- Prometheus, Grafana, OpenTelemetry for observability
- Istio service mesh for mTLS and zero-trust networking
- HashiCorp Vault for secrets management

## Development Setup

- Install Kubernetes cluster (EKS or GKE) with GPU node group
- Set up Helm for deploying microservices
- Configure Istio service mesh with mTLS STRICT mode
- Deploy Kafka cluster for event streaming
- Build and deploy Docker containers for each microservice
- Set up Redis cache and Vault for secrets
- Run React frontend with Vite development server
- Configure Prometheus and Grafana for monitoring

## Technical Constraints

- Latency must be ≤ 1 second from audio ingestion to suggestion display
- Word error rate target ≤ 7% on accented English
- All services must run non-root with strict security policies
- No .env files in container images; secrets injected via Vault
- Network egress DENY by default; only allow required service communication

## Dependencies

- Kubernetes cluster with GPU support
- Kafka messaging system
- Redis cache server
- HashiCorp Vault for secrets
- Docker and Helm for containerization and deployment
- React and Vite for frontend development
- Prometheus and Grafana for observability

## Tool Usage Patterns

- Use Helm charts for deploying and managing microservices
- Use GitHub Actions for CI/CD pipelines
- Use ArgoCD for GitOps deployment automation
- Use OpenTelemetry for tracing gRPC calls
- Use Falco sidecar for runtime security monitoring
- Use Trivy for container image vulnerability scanning
