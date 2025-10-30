# Alma Emotional Map v0.1

**Purpose:**  
Define a minimal, shared emotional model for Alma so that sensing, backend processing, and UI/UX can all talk the same language. This is NOT the final emotional ontology — it’s the first operational version.

---

## 1. Core Emotional States

1. **Resonance**
   - Meaning: user is emotionally and physiologically aligned.
   - Physiological markers: HR stable (within personal baseline), GSR low-variance, clean signal.
   - Alma response: soft haptic pulse (1x), green visual tone, short “you’re in sync” message.
   - Notes: this state should be logged as a positive sample for future ML.

2. **Tension**
   - Meaning: user is entering a sympathetic/alert state.
   - Physiological markers: HR ↑ or HRV ↓, GSR spikes, micro-instability in signal.
   - Alma response: grounding suggestion (breathe 1 cycle), amber visual tone, optional voice hint.
   - Notes: trigger alert only on 2 consecutive breaches (debounce).

3. **Flow**
   - Meaning: engaged but not stressed.
   - Physiological markers: HR in mid-range, GSR adaptive, cadence steady.
   - Alma response: minimal — only monitoring. No interruption.
   - Notes: this is a desirable working state; should NOT be confused with stress.

4. **Fatigue**
   - Meaning: system is slowing down / user is under-recovered.
   - Physiological markers: HR slightly ↓, variability low, signal “flat”.
   - Alma response: “soft break” suggestion, blue/teal visual tone, possible long-term insight (“you’ve been low for 30m”).
   - Notes: can be used for recovery analytics.

5. **Overload**
   - Meaning: too many stress signals at once OR poor signal quality.
   - Physiological markers: unstable HR + unstable GSR, signal_lost events, rapid changes.
   - Alma response: pause insights, ask for better contact (“adjust device”), red/alert tone.
   - Notes: don’t push insights on bad data.

6. **Calm Recovery**
   - Meaning: user is coming back to baseline after stress.
   - Physiological markers: HR normalizing, GSR settling.
   - Alma response: quick reinforcement (“good, you’re back”), green/teal tone.
   - Notes: log as successful regulation.

---

## 2. Processing & Windows

- Base cadence (canonical): **2 seconds** ingestion.
- Rolling windows: **6 minutes**, **10–12 minutes**, **30 minutes**.
- Debounce rules:
  - HR_HIGH / HR_LOW → require 2 consecutive windows
  - signal_lost → if no data ≥ 10 minutes
  - battery_low → < 20%
- Resampling: **only for UI**, not for core analysis.
- Each insight must have a **confidence score**.

---

## 3. Feedback Layer (User-Facing)

- Haptic: single / double pulse, never continuous.
- Visual: forest-green palette as default, amber for tension, red only for technical issues.
- Audio/voice: optional, short, supportive, non-dominant.
- Timing: prefer **periodic feedback** over spammy/continuous nudging.

---

## 4. Notes for Engineering (Saurabh)

- This map is the reference for labeling raw data.
- Each state above can be an enum, e.g. `ALMA_STATE_RESONANCE`, `ALMA_STATE_TENSION`, etc.
- Store insights with: `timestamp`, `state`, `confidence`, `source_window`.
- UI can subscribe to state changes via websocket / pub-sub later.
- Do NOT block processing if one sensor is missing; degrade gracefully.
