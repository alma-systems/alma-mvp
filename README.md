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
## Core Architecture

Alma’s architecture follows a modular and signal-driven design — built to translate human physiological and emotional data into coherent feedback loops.

### 🧠 Layer Overview

**1. Frontend Layer (User Interaction)**
- Built with Next.js (v14+)
- Real-time UI for emotional state reflection
- Displays live cadence visualization (2-min baseline)
- Handles haptic/light feedback mapping

**2. Backend Layer (Signal Processing)**
- API built with FastAPI or Node.js
- Ingests sensor data (HR, HRV, GSR, temperature, accelerometer)
- Performs rolling window analysis (6, 10–12, and 30 min)
- Applies debounce rules for false-positive prevention

**3. Data Layer**
- Stores and timestamps all signals with confidence scores
- Maintains session continuity and anomaly tracking
- Supports export in JSON/CSV for lab integrations

**4. Feedback Layer (Alma Engine)**
- Converts processed signals into emotional insights
- Triggers feedback events (light, haptic, or sound)
- Uses confidence-weighted emotional states to avoid noise

---

### ⚙️ Core Logic Flow


- 2-minute cadence defines data sampling rate  
- Debounce logic triggers only after 2 consistent anomalies  
- Confidence score adjusts output intensity (0.0–1.0 scale)  

---

### 🪶 System Safety Rules
- `signal_lost` → trigger if no data ≥10 min  
- `battery_low` → trigger if battery <20%  
- Automatic fallback to “neutral feedback mode” when coherence < threshold  

---

### 🔄 Current Focus
- Integrate `confidence_score` logic into backend  
- Optimize data smoothing for high-motion users  
- Prepare MVP testing for haptic feedback alignment
