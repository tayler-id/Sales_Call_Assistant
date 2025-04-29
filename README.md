# Sales Call Assistant

## Overview

The Sales Call Assistant is a production-grade, real-time AI sales assistant designed to provide ultra-low latency speech-to-text transcription and actionable sales suggestions during live calls. This system leverages advanced AI models, a scalable microservices architecture, and secure, observable infrastructure to deliver measurable improvements in sales performance.

## Features

- Real-time streaming speech-to-text using Whisper-T GPU pods.
- NLP prompt orchestration with GPT-5 / Claude-Next.
- Fine-tuned suggestion engine with Redis caching.
- React + Vite frontend with live transcript and floating suggestion cards.
- Secure microservices communication with Istio mTLS and zero-trust networking.
- Export connectors for HubSpot, Salesforce, and Pipedrive.
- Comprehensive observability with Prometheus, Grafana, OpenTelemetry, and Falco.
- CI/CD pipelines with GitHub Actions, Cosign signing, and ArgoCD GitOps deployment.

## Architecture

The system consists of 10 core microservices deployed on a Kubernetes cluster with GPU and CPU node groups. Services communicate via gRPC and Kafka topics, secured with strict policies. The frontend connects via WebSocket for live updates.

## Getting Started

Refer to the `memory-bank/implementationPlan.md` for detailed setup instructions, development milestones, and deployment guidelines.

## Repository Structure

- `memory-bank/` - Core project documentation and planning files.
- `src/` - Source code for microservices and frontend (to be implemented).
- `charts/` - Helm charts for Kubernetes deployment (to be implemented).
- `docs/` - Additional documentation and resources.

## Contributing

Contributions are welcome. Please follow the established coding standards and security practices outlined in the project documentation.

## License

[Specify license here]

## Contact

For questions or support, please contact [Your Contact Information].
