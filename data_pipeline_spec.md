# Alma – Data Pipeline Specification

## Purpose
The data pipeline is responsible for transforming raw physiological and emotional sensor inputs into coherent, interpretable emotional states.  
It operates under Alma’s cadence framework, ensuring consistent timing, reliability, and emotional accuracy.

---

## 1. Signal Acquisition

**Sensors & Inputs**
- Heart Rate (HR)
- Heart Rate Variability (HRV)
- Galvanic Skin Response (GSR)
- Skin Temperature (TEMP)
- Accelerometer / Motion
- (Optional) Audio / Voice micro-signals

**Sampling Rate**
- Base: every **2 minutes**
- Rolling windows: **6 min**, **10–12 min**, and **30 min**
- Sampling buffer: 3 readings minimum per window

---

## 2. Data Normalization

**Process**
- Raw input → scaled to 0.0–1.0 range  
- Outlier removal using z-score > 3  
- Missing data interpolated linearly (max gap = 3 min)  
- Motion artifacts corrected via accelerometer filtering  

**Output**
```json
{
  "timestamp": "2025-10-28T20:00:00Z",
  "hr": 74,
  "hrv": 0.83,
  "gsr": 0.27,
  "temp": 36.2,
  "confidence": 0.91
}
