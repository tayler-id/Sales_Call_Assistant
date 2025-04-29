# Project Brief

This document serves as the foundational document for the project, outlining its core requirements and goals.

## Project Name

Sales Call Assistant - Production-Grade Real-Time AI Sales Assistant

## Project Goals

- Build a production-grade real-time AI sales assistant with ultra-low latency.
- Achieve ≤ 1 second tip latency from utterance to on-screen suggestion.
- Maintain word error rate ≤ 7% on accented English.
- Deliver measurable sales KPI improvements with AI guidance.
- Ensure secure, scalable, and observable microservices architecture.

## Core Requirements

- Hardened architecture with 10 core microservices.
- Secure communication with mTLS and zero-trust networking.
- Scalable infrastructure using Kubernetes and GPU nodes.
- Real-time streaming speech-to-text with Whisper-T GPU pods.
- NLP prompt orchestration using GPT-5 / Claude-Next.
- Suggestion engine with fine-tuned LLM and Redis caching.
- Frontend React + Vite UI with WebSocket live updates.
- Export connectors for CRM systems (HubSpot, Salesforce, Pipedrive).
- Observability stack with Prometheus, Grafana, OpenTelemetry.

## Stakeholders

- Sales teams seeking AI-driven call assistance.
- Software engineers building and maintaining the system.
- Product managers overseeing feature delivery.
- Security and operations teams ensuring compliance and uptime.

## Initial Scope

Build and deploy the 10 core microservices with end-to-end streaming, real-time suggestions, and frontend UI. Implement security hardening and observability. Pilot with target niche users.

## Out of Scope

- Billing and payment integration (planned for later phases).
- Support for languages beyond English (initially).
- Offline or batch processing modes.

## Key Deliverables

- Fully containerized microservices with Helm charts.
- Kubernetes cluster with GPU and CPU node groups.
- React frontend with live transcript and suggestion UI.
- Export jobs producing CSV and PDF reports.
- Security and observability tooling integrated.
