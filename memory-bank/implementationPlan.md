# Sales Call Assistant Implementation Plan

This document outlines the detailed plan to implement the production-grade Sales Call Assistant system based on the provided blueprint.

## 1. Microservices Implementation

- Implement 10 core microservices:
  - Ingestion Gateway (API-GW with TLS and auth)
  - Audio Buffer (Edge Worker with WebRTC/UDP)
  - STT Microservice (Whisper-T GPU pod with gRPC streaming)
  - NLP Prompt Orchestrator (GPT-5 / Claude-Next)
  - Suggestion Engine (Fine-tuned LLM with Redis cache)
  - Realtime API (WebSocket fan-out with elastic scaling)
  - Frontend (React + Vite / Electron)
  - Summary/Insights Job (Batch export to PDF/CSV)
  - Export Connector (HubSpot, Salesforce, Pipedrive)
  - Observability Stack (Prometheus, Grafana, Falco, OpenTelemetry)

- Containerize each service with distroless images.
- Create Helm charts for Kubernetes deployment.
- Deploy STT service on GPU node group; others on CPU nodes.
- Use Kafka topics for event streaming between services.
- Secure all communication with Istio mTLS and zero-trust policies.

## 2. Security & Operations Hardening

- Drop all Linux capabilities except NET_BIND_SERVICE.
- Run containers as non-root UID 1000.
- Enforce AppArmor and Falco runtime security policies.
- Use HashiCorp Vault for secrets management with short-lived tokens.
- Deny all network egress by default; allow only required service communication.
- Scan images with Trivy and sign with Cosign.
- Use GitHub Actions for CI/CD with security checks.
- Deploy with ArgoCD GitOps.

## 3. CI/CD Pipeline

- Build, test, and scan containers in GitHub Actions.
- Sign images with Cosign.
- Deploy to Kubernetes via ArgoCD.
- Implement rollback and monitoring strategies.

## 4. Frontend Development

- Build React + Vite UI with:
  - Live scrollable transcript display.
  - Floating 'Whisper-card' suggestions with auto-fade.
  - Hotkey (Ctrl+Shift+Space) to copy tips to clipboard.
- Connect frontend to Realtime API WebSocket.

## 5. Observability Integration

- Add OpenTelemetry tracing to all gRPC calls.
- Export OTLP data to collector.
- Create Grafana dashboards for latency, word-error-rate, suggestion-accept-rate.
- Set Prometheus alerts for p95 latency and API error rates.
- Use Falco sidecar for runtime security monitoring.

## 6. Export Connectors

- Implement batch export jobs producing CSV and PDF reports.
- Integrate with HubSpot, Salesforce, and Pipedrive.

## 7. 12-Week Execution Calendar

| Week | Milestone                                         |
|-------|-------------------------------------------------|
| 1     | Repo setup, GitHub Actions, Terraform skeleton  |
| 2     | Kubernetes cluster online; Istio, Vault operational |
| 3     | Whisper-T service containerized; latency bench ≤0.8 s |
| 4     | Kafka topics + NLP orchestrator prototype        |
| 5     | React UI first light; WebSocket pipeline end-to-end smoke |
| 6     | Suggestion templates tuned on 25 dummy calls     |
| 7     | Export job producing CSV & PDF; nightly batch verified |
| 8     | Security hardening pass; Trivy score 0 critical CVEs |
| 9     | Observability dashboards + alert rules live      |
| 10    | Pilot with 5 real estate agents (target niche)   |
| 11    | Feedback loop → prompt tweaks, UI polish          |
| 12    | Billing stripe integration; ready for paid beta   |

## 8. Risks and Mitigations

- Achieving sub-second latency requires optimized streaming and caching.
- Security policies may impact deployment complexity; thorough testing needed.
- Observability integration critical for early issue detection.

---

This plan aligns with the project goals and technical constraints documented in the memory bank. It provides a clear roadmap for building a scalable, secure, and production-ready AI sales assistant.
