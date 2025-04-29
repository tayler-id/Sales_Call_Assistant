# Product Context

This document describes the purpose of the project, the problems it solves, how it should work, and the user experience goals.

## Purpose

To build a production-grade real-time AI sales assistant that provides ultra-low latency, accurate speech-to-text transcription, and actionable sales suggestions during live calls.

## Problems Solved

- High latency and inaccuracy in existing speech-to-text solutions for sales calls.
- Lack of real-time, context-aware sales guidance during calls.
- Difficulty in scaling and securing AI-driven microservices for live applications.
- Integration challenges with CRM and sales tools for exporting insights.

## How it Should Work

The system ingests live audio streams, processes them through a low-latency Whisper-T STT service, orchestrates NLP prompts with GPT-5/Claude-Next, and delivers real-time sales suggestions via a React frontend. It supports export connectors and observability tooling for operational excellence.

## User Experience Goals

- Real-time display of call transcripts with minimal delay.
- Floating suggestion cards that provide actionable sales tips.
- Easy-to-use UI with hotkeys for quick tip copying.
- Reliable and secure operation with seamless integration into sales workflows.

## Target Audience

- Sales professionals seeking AI assistance during calls.
- Sales managers monitoring team performance.
- Developers and operators maintaining the system.
