## ⚡ Adaptive Multi-Point Power Theft & Line-Fault Detection System

A low-cost, edge-based system for detecting and classifying power line anomalies using
ESP32 microcontrollers and CT current sensors distributed along a feeder line.

### Key Features
- 🧠 **Self-learning baseline** — adaptively learns normal current-loss patterns, but
  updates *only* during verified-normal conditions, preventing slow theft events from
  being learned as "normal"
- 🔍 **Multi-class event classification** — distinguishes **power theft**, **line fault**,
  **sensor failure**, and **communication failure** using mismatch magnitude, duration,
  and waveform behavior
- 📍 **Feeder segment localization** — pinpoints the exact segment of the line affected,
  not just that an anomaly exists
- 📲 **Real-time alerts** — sends SMS/mobile app notifications via GSM on detection

### Hardware
ESP32 · CT sensors (SCT-013) · GSM module (SIM800L) · Wi-Fi/ESP-NOW

### Status
🚧 Lab-scale prototype / undergraduate research project
