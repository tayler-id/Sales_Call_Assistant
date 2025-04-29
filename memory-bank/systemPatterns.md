# System Patterns

This document outlines the system architecture, key technical decisions, design patterns in use, component relationships, and critical implementation paths.

## Architecture Overview

The system is composed of 10 core microservices deployed on a Kubernetes cluster with GPU and CPU node groups. Services communicate via gRPC and Kafka topics with mTLS enforced. The frontend is a React + Vite application connecting via WebSocket for real-time updates.

## Key Technical Decisions

- Use Whisper-T GPU pods for low-latency streaming STT.
- Employ Kafka for decoupled, scalable event streaming.
- Use GPT-5 / Claude-Next for NLP prompt orchestration.
- Redis caching for suggestion engine to reduce latency.
- Secure all service communication with Istio mTLS and zero-trust policies.
- Containerize all services with distroless images and enforce runtime security with AppArmor and Falco.

## Design Patterns

- Microservices architecture with event-driven communication.
- Edge worker pattern for audio buffering and WebRTC ingestion.
- CQRS pattern separating read and write workloads in suggestion engine.
- Circuit breaker and retry patterns for resilient service calls.
- Observability with OpenTelemetry tracing and Prometheus metrics.

## Component Relationships

- Ingestion Gateway receives audio streams and forwards to Audio Buffer.
- Audio Buffer publishes raw audio to Kafka topic consumed by STT Microservice.
- STT Microservice streams words to NLP Prompt Orchestrator.
- NLP Prompt Orchestrator sends suggestions to Suggestion Engine.
- Suggestion Engine caches and pushes suggestions to Realtime API.
- Frontend subscribes to Realtime API WebSocket for live updates.
- Summary/Insights Job consumes Kafka topics for batch exports.
- Export Connector integrates with CRM systems.
- Observability Stack collects telemetry from all services.

## Critical Implementation Paths

- Real-time audio ingestion → STT transcription → NLP prompt orchestration → suggestion delivery → frontend display.
- Security enforcement across all service communications.
- Export job batch processing and CRM integration.
- Observability data collection and alerting.
