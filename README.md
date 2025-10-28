# Alma v0.1 — Emotional AI Companion (MVP)

Translating emotion into clear, helpful interactions.

## Scope (MVP)
- Web chatbot (text-only)
- One-page website (About, Chat, Contact)
- Slim backend API; future sensor integration

## Structure
- /frontend  – Next.js app (chat UI)
- /backend   – FastAPI or Node API
- /docs      – specs & notes
- /design    – logo, palette

## Principles
Simple. Reliable. Testable. Ship MVP, then iterate.
# ALMA – Emotional Resonance System

**Mission:**  
To translate emotional and physiological signals into meaningful, interpretable feedback — a bridge between data and feeling.

## Core Principles
- 2-minute cadence for live data capture  
- Rolling windows: 6, 10–12, and 30 minutes  
- Debounce logic for HR_HIGH / HR_LOW alerts (2 consecutive readings)  
- Signal integrity: `signal_lost` > 10 min, `battery_low` < 20%  
- Confidence score applied per insight  

## Endpoints
- `/ingest` – data input from sensors  
- `/coherence` – signal alignment and processing  
- `/insight` – emotional/physiological feedback output  

## Next Steps
- Integrate confidence score logic  
- Connect ClickUp task tracking  
- Finalize data pipeline specification
