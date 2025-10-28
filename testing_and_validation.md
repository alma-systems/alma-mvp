# ALMA – Testing and Validation Plan

## Purpose
To ensure the reliability, safety, and interpretive accuracy of Alma’s emotional resonance system.  
Testing covers both the hardware and software components of the MVP.

---

## 1. Test Environments

| Environment | Description |
|--------------|-------------|
| **Lab Mode** | Controlled conditions for signal accuracy testing |
| **Field Mode** | Real-world use (daily wear, movement, noise, temperature variance) |
| **Simulation Mode** | Injected synthetic data to stress-test algorithms |

---

## 2. Hardware Validation

| Component | Test | Expected Result |
|------------|------|-----------------|
| Heart Rate Sensor | Readings ±2 BPM from reference | Stable HR trace |
| GSR Sensor | Correlates with skin moisture / stress | Detectable response in <2s |
| Temperature Sensor | ±0.3°C accuracy | Smooth trend over time |
| Accelerometer | Detects orientation / movement | No false triggers |
| BLE Communication | Data packet integrity test | 100% delivery rate over 2m distance |

---

## 3. Software Validation

**Signal Pipeline Tests**
- ✅ Rolling window calculations (6, 12, 30 min)
- ✅ Debounce rule accuracy (two consecutive anomalies only)
- ✅ Confidence score scaling between 0.0–1.0
- ✅ `signal_lost` trigger when no data ≥10 min

**API Tests**
- `/ingest` accepts valid JSON data and rejects malformed inputs  
- `/coherence` returns correct computed score  
- `/insight` generates state output with correct confidence  

---

## 4. Performance Metrics

| Metric | Target | Validation Method |
|---------|---------|-------------------|
| Data latency | < 2 sec | End-to-end test |
| Signal accuracy | > 95% compared to lab instruments | Cross-validation |
| False-positive alerts | < 5% | Controlled HR variation tests |
| Battery duration | ≥ 12 hours | Continuous operation |
| BLE stability | ≥ 98% uptime | 24-hour stress test |

---

## 5. Emotional Coherence Testing

| Scenario | Expected System Response |
|-----------|--------------------------|
| Rapid HR rise (stress) | GSR ↑, coherence ↓ → amber flicker feedback |
| Deep breathing (relaxation) | HRV ↑, coherence ↑ → green steady glow |
| Sudden motion | Accelerometer detects noise → debounce applied |
| No signal (band off) | `signal_lost` → white fade-out |
| Reconnection | `recovered` → green fade-in |

---

## 6. User Feedback Validation

**Qualitative Testing**
- 5–10 users wear Alma for 48h.  
- Journal emotional states manually.  
- Compare subjective feelings vs. Alma’s recorded states.  

**Quantitative Testing**
- HRV correlation coefficient ≥ 0.7 with reference device.  
- Emotional prediction accuracy ≥ 80% agreement with user logs.  

---

## 7. Known Issues (to monitor)
- Motion artifacts during running or handwashing.  
- Temperature sensor drift in cold environments.  
- Slight delay (1–2s) in haptic response after BLE reconnection.  

---

## 8. Next Steps
- Automate regression tests for `/coherence` and `/insight` endpoints.  
- Integrate “coherence history” graphs for test reporting.  
- Establish external validation protocol with partner labs.

---

**Version:** 1.0  
**Maintainer:** Adelina Luca – Alma Systems  
**Last Updated:** 2025-10-28
