# Alma Edge Case Matrix v0.1

**Purpose:**  
To define how Alma detects, manages, and gracefully recovers from abnormal sensor or signal situations.  
The goal is not to eliminate anomalies but to respond with stability and awareness.

---

## 🧭 Guiding Principle
> "Every disruption is a signal — not an error."  
Alma interprets edge cases as opportunities for recalibration and learning.

---

## ⚙️ Detection Categories

| Edge Case | Possible Cause | Detection Rule | Expected System Behavior | Recovery Strategy |
|------------|----------------|----------------|---------------------------|-------------------|
| **Signal Lost** | Disconnected sensor / low battery | No data ≥ 10 min | Trigger `signal_lost` event | Reconnect / wait for reconnection |
| **False HR Spike** | Motion artifact / poor contact | HR jump > 35% baseline for < 10s | Ignore (debounce rule applies) | Maintain previous stable HR |
| **Cold Skin / Low EDA** | Peripheral vasoconstriction | EDA < 0.1 µS for > 2min | Flag as `low_eda_state` | Blend HRV signal for compensation |
| **Movement Interference** | Walking / cleaning / carrying | Accelerometer variance > threshold | Suspend coherence computation | Resume after motion stabilizes |
| **Sensor Drift** | Long use / sweat accumulation | Gradual offset in HR or EDA baseline | Auto-recalibrate baseline | Update calibration every 30 min |
| **High Stress + Calm Context** | Cognitive vs. physical mismatch | HR↑ + HRV↓ + EDA↑ + low activity | Mark as `ambiguous_state` | Delay feedback; cross-check user context |
| **Long Idle (No Change)** | User asleep / resting | HR & EDA stable > 60min | Enter low-frequency mode | Reduce sampling; wait for trigger |
| **Device Off / Reboot** | Power cycle | Data stream reset | Log session break | Resume as new session |

---

## 🧮 Logging Fields
{
"timestamp": "...",
"event_type": "edge_case",
"case_name": "signal_lost",
"duration_sec": 600,
"resolved": true,
"recovery_time_sec": 42
}

---

## 🌀 Integration
- The **Edge Case Handler** runs parallel to the **Neural Bridge**.  
- When triggered, it pauses the Coherence Spiral computation and preserves context.  
- If the case persists >3 cycles → alert backend → trigger soft Murmur vibration (haptic notification).

---

## 📚 Future Notes
- Expand detection with accelerometer + temperature correlation  
- Add adaptive thresholds per user  
- Include synthetic edge cases for ML robustness testing

---

**Version:** 0.1  
**Author:** Raluca Adelina Luca  
**Date:** 31 October 2025

Each edge case is logged with:

