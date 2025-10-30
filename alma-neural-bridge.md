# Alma Neural Bridge v0.1

**Purpose:**  
To define how raw biometric signals (HR, HRV, EDA, temperature, contact pressure) are transformed into emotional state data used by Alma’s Emotional Map.

---

## ⚙️ Core Flow
**Signal → Preprocessing → Normalization → Feature Extraction → Emotional Inference → State Update**

---

## 1. Signal Input
| Source | Sensor Type | Sampling Rate | Output |
|---------|--------------|----------------|---------|
| HR | PPG / ECG | 2-min cadence | bpm |
| HRV | derived from HR | rolling 6-min window | RMSSD, LF/HF |
| EDA | skin conductance | 1Hz | µS |
| Temperature | skin / ambient | 0.2Hz | °C |
| Contact Pressure | tactile patch | 1Hz | N/cm² |

---

## 2. Preprocessing
- **Noise filtering:** adaptive moving average  
- **Interpolation:** handles signal gaps under 10s  
- **Debounce rule:** 2 consecutive breaches needed to confirm HR_HIGH / HR_LOW events  
- **Signal lost:** if no data ≥10min → triggers `signal_lost` flag

---x_norm = (x - μ) / σ
This ensures cross-user emotional consistency.

---

## 4. Emotional Inference
| Physiological Pattern | Emotional Marker | Confidence Range |
|------------------------|------------------|------------------|
| ↑HR + ↑EDA + ↓HRV | Stress / Overwhelm | 0.75–0.9 |
| ↓HR + ↑HRV | Calm / Grounded | 0.8–0.95 |
| ↑HR + ↑HRV | Excitement / Joy | 0.7–0.85 |
| Stable HRV + stable EDA | Focus / Flow | 0.9–1.0 |

---

## 5. State Update
When a new emotional state is detected, the bridge sends:
{
"timestamp": "...",
"signal_origin": "biosensor_id",
"state_change": {
"from": "focus",
"to": "calm",
"confidence": 0.91
}
}

---

## 🔄 Feedback Loop
If confidence < 0.7, system queries the **Coherence Spiral** for context validation (e.g., “Is user moving or meditating?”).

---

## 📚 Future Extension
- Add multimodal fusion (voice tone + gesture sensor)
- Integrate with Alma’s haptic feedback (Murmur)
- Emotional latency tracking for predictive regulation

---

**Version:** 0.1  
**Author:** Raluca Adelina Luca  
**Date:** 30 October 2025


## 3. Feature Normalization
Each feature is rescaled to [0,1] based on rolling mean and standard deviation:
