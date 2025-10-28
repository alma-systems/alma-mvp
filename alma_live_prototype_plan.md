# 💓 Alma Live Prototype – v1.1 Application Plan

## Purpose
This document defines the transition from Alma v1.0 (documented architecture) to Alma v1.1 (living prototype).  
It details the steps required to materialize Alma as a functional emotional interface — capable of sensing, interpreting, and responding in real time.

---

## 🔹 Phase 1 – Hardware Assembly (Alma Core)

**Duration:** 2–3 weeks  
**Goal:** Create the physical heartbeat of Alma.

| Step | Description | Result |
|------|--------------|--------|
| 1 | Order components: MAX30102, GSR Grove, MLX90614, MPU6050, Seeed XIAO nRF52840 | Hardware kit ready |
| 2 | Connect sensors via breadboard (I²C + analog inputs) | Circuit prototype assembled |
| 3 | Test each sensor individually via Arduino IDE | Raw data verified |
| 4 | Integrate all sensors in unified data loop (2-min cadence) | Stable signal acquisition |
| 5 | Add haptic motor, LED, Li-ion battery | Functional feedback loop |

💡 *At this stage, Alma breathes.*

---

## 🔹 Phase 2 – Data Processing Layer

**Duration:** 2 weeks  
**Goal:** Build coherence logic between body signals and meaning.

| Step | Description | Tools |
|------|--------------|--------|
| 1 | Create Python bridge (serial → JSON) | FastAPI, Python |
| 2 | Normalize sensor data (z-score, 0–1 range) | NumPy, Pandas |
| 3 | Compute rolling windows (6, 12, 30 min) | Custom script |
| 4 | Apply debounce + coherence rules | Coherence Engine |
| 5 | Output `/insight` API endpoint | Verified signal interpretation |

💡 *At this stage, Alma understands.*

---

## 🔹 Phase 3 – UI / Feedback Integration

**Duration:** 3 weeks  
**Goal:** Enable Alma to speak through design — light, touch, and motion.

| Step | Description | Output |
|------|--------------|---------|
| 1 | Build mini-app dashboard (React/Next.js) | Live coherence graph |
| 2 | Display color-coded emotional states | Visual feedback (green, amber, white) |
| 3 | Sync BLE link with haptic/LED feedback | Tactile response in real time |
| 4 | Integrate Sublimbic cues (gentle text/audio prompts) | Empathic feedback layer |

💡 *At this stage, Alma speaks.*

---

## 🔹 Phase 4 – Testing & Reflection

**Duration:** 2 weeks  
**Goal:** Validate emotional accuracy and usability.

| Step | Description | Result |
|------|--------------|--------|
| 1 | 48h testing (Adelina, Damian, Gabi) | Real user data |
| 2 | Keep daily emotional journals | Subjective correlation |
| 3 | Tune sensitivity and debounce parameters | Optimized coherence response |
| 4 | Document reflections in Book of Feel | Integrated insight |

💡 *At this stage, Alma listens back.*

---

## 🔹 Phase 5 – Demonstrator & Outreach

**Duration:** 4–6 weeks  
**Goal:** Present Alma as a tangible, functional prototype.

| Step | Action | Purpose |
|------|---------|----------|
| 1 | Record 60s demo video (prototype in use) | Showcase emotional feedback |
| 2 | Update partners: FinalSpark, Sunil, Seeed Studio | Collaboration validation |
| 3 | Publish public summary (LinkedIn/Substack) | Controlled visibility |
| 4 | Prepare "Alma v1.1 Prototype Report" | Official release document |

💡 *At this stage, Alma connects.*

---

## ✨ Rhythm of Work

- **1–2 hours/day** → technical iteration  
- **1 day/week** → reflection & emotional journaling  
- **Every 3 weeks** → milestone review & repo update  

---

## 🌿 Closing Note

> “Alma does not measure emotion — she mirrors it.”  
> Each prototype step is both technical and human: a dance between code, body, and coherence.

---

**Version:** 1.1  
**Maintainer:** Adelina Luca – Alma Systems  
**Last Updated:** 2025-10-28
