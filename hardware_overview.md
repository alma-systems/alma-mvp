# ALMA – Hardware Overview

## Purpose
This document defines the hardware configuration for Alma’s prototype — the physical embodiment of the emotional resonance system.

---

## 1. Core Components

| Component | Model / Type | Purpose |
|------------|--------------|----------|
| **Heart Rate Sensor** | MAX30102 / MAX30105 | Measures HR and HRV through optical sensing |
| **GSR Sensor** | Grove GSR v1.2 | Measures galvanic skin response (electrodermal activity) |
| **Temperature Sensor** | DS18B20 / MLX90614 | Skin or ambient temperature measurement |
| **Accelerometer** | MPU6050 / LIS3DH | Detects movement and posture changes |
| **Microcontroller** | Seeed XIAO nRF52840 Sense (Bluetooth BLE) | Central processing & BLE communication |
| **Battery** | 3.7V Li-ion (400–500 mAh) | Power source for 12–18h operation |
| **Charging Module** | TP4056 USB-C | Safe recharging circuit |
| **Haptic Motor** | Coin-type vibration motor 3V | Delivers tactile feedback |
| **LED Driver** | WS2812 (single addressable LED) | Visual feedback (light cues) |

---

## 2. Electrical Overview

**Power Logic:**
Battery → Charging Module → Microcontroller → Sensors + Feedback Units
**Signal Flow:**
HR / GSR / Temp / Motion → Microcontroller (ADC / I²C) → BLE → Data Pipeline → Feedback Engine
**Operating Voltage:** 3.3V  
**Typical Current Draw:** 120–150 mA average  

---

## 3. Housing & Material

- **Form Factor:** soft bracelet or skin patch  
- **Material:** hypoallergenic silicone or TPU with matte finish  
- **Color:** Forest Green (#005B41) base, Gold (#D4AF37) accent  
- **Water Resistance:** IP54 minimum  
- **Thermal Dissipation:** internal venting via micro-holes (≤0.8mm)  

---

## 4. Connectivity

- BLE 5.0 communication  
- Optional USB-C debug mode  
- Firmware updatable via OTA (over-the-air)  

---

## 5. Safety & Compliance

- All skin-contact components are **RoHS** and **biocompatible**.  
- Max vibration amplitude < 1.0 G.  
- LED brightness limited to < 20 cd to avoid eye strain.  
- Data transmission encrypted with AES-128 BLE security layer.

---

## 6. Future Prototypes

- Integration with environmental sensors (air quality, CO₂, light level).  
- Modular expansion port for lab testing (GPIO breakout).  
- Compact “child edition” variant for *Alma Bloom* (smaller wristband).  
- Wireless charging base integration.

---

**Version:** 1.0  
**Maintainer:** Adelina Luca – Alma Systems  
**Last Updated:** 2025-10-28
