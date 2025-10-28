# ALMA – UI Feedback Logic

## Purpose
This document defines how Alma communicates emotional coherence and physiological feedback to the user through light, vibration, and sound.  
The interface is designed to be non-invasive, intuitive, and emotionally legible.

---

## 1. Design Principles

| Principle | Description |
|------------|-------------|
| **Subtlety over stimulation** | Alma should never startle the user — feedback must feel like a whisper, not an alarm. |
| **Consistency** | Similar emotional states should produce the same tactile and visual patterns. |
| **Meaningful silence** | Sometimes, *no feedback* is the right feedback — coherence is presence. |
| **Harmony of channels** | Light, vibration, and sound never contradict each other; they form a single rhythm. |

---

## 2. Feedback Channels

### 💡 Light (Visual Feedback)
- **Base color:** Forest Green (#005B41) – represents equilibrium.  
- **Accent color:** Gold (#D4AF37) – used during high coherence moments.  
- **Dynamic range:**
  - Calm → steady dim glow (green)
  - Neutral → slow pulse (soft green)
  - Distress → brief amber flicker (low intensity)

### 🔊 Sound (Auditory Feedback)
- Ambient tone, never exceeding 40 dB.
- Frequencies:
  - Calm → 432 Hz harmonic pulse (heart alignment)
  - Neutral → 528 Hz soft modulation
  - Distress → 250 Hz short tone, fades in 1.2 sec
- Optional “breath alignment” rhythm – mimics 6 bpm slow breathing.

### 🤲 Haptic (Tactile Feedback)
- Calm → subtle 0.2s vibration every 30s
- Neutral → 0.4s vibration every 20s
- Distress → quick 0.8s pulse repeated twice, then pause
- Transition smoothing: vibration strength scaled by confidence score (0.0–1.0)

---

## 3. Mapping Emotional States to Feedback

| State | Light | Haptic | Sound | Symbolic Meaning |
|--------|--------|---------|--------|-----------------|
| Calm | steady soft green | low vibration | harmonic tone 432 Hz | coherence achieved |
| Neutral | pulsing green | medium vibration | subtle modulation | observing phase |
| Distressed | amber flicker | stronger pulse | low tone 250 Hz | regulation needed |
| Signal Lost | white fade-out | one long pulse | no sound | disconnection detected |
| Reconnection | green fade-in | short vibration | brief harmonic tone | coherence restored |

---

## 4. Technical Notes
- All feedback is **synchronized to the 2-minute cadence** for consistency.  
- The **confidence score** adjusts intensity and duration:
  - Low confidence → subtle feedback
  - High confidence → clear, longer patterns  
- A **neutral fallback mode** activates if coherence < 0.3 for 3 consecutive readings.

---

## 5. Future Extensions
- Adaptive learning of user preference (light vs. haptic emphasis)
- Emotional signature visualization (pattern replay for reflection)
- “Silent mode” for night use (haptic only)
- Voice cue integration (“breathe,” “pause,” “release”)

---

**Version:** 1.0  
**Maintainer:** Adelina Luca – Alma Systems  
**Last Updated:** 2025-10-28
