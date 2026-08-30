# ⚡ PowerLoss Sentinel

> **Predictive, Explainable, and Segment-Level Grid Intelligence for Emerging Distribution Energy Loss**

PowerLoss Sentinel is an edge-intelligent IoT decision-support system designed to monitor electrical distribution feeders in real time. By deploying distributed sensing nodes along secondary feeder segments, the system learns localized behavioral profiles, detects early anomaly trends, isolates root causes, and alerts utility personnel before minor mismatches escalate into critical losses or feeder failures.

---

## 📌 Problem Overview

Distribution utilities lose millions annually to technical and non-technical losses (NTLs) such as unauthorized tapping, meter tampering, equipment degradation, and sensor drift. Existing solutions suffer from three major issues:
1. **Delayed Detection:** Anomalies are often identified weeks or months later during billing reconciliations.
2. **Poor Localization:** Traditional systems flag that a broad grid area has high loss, but fail to pinpoint the physical line segment responsible.
3. **High False Alarms:** Normal demand surges, technical impedance, sensor miscalibrations, and active theft yield overlapping signals that confuse traditional static threshold systems.

---

## 🧠 Core System Capabilities

### 1. Adaptive Self-Learning Baseline
* Learns the dynamic, temporal consumption fingerprint of individual feeder segments.
* **Gated Updating Mechanism:** Model updates occur *only* during verified-normal system states, preventing slow, incremental theft from being gradually absorbed into the "normal" baseline.

### 2. Multi-Class Event Classification
* Analyzes current mismatch magnitude, anomaly duration, phase relationships, and waveform anomalies.
* Accurately differentiates between **Power Theft**, **Line Faults**, **Sensor Failures**, and **Communication Losses**.

### 3. Feeder Segment Localization
* Divides the distribution line into localized sub-segments monitored by edge node pairs.
* Calculates real-time differential loss across consecutive nodes to isolate problem locations down to specific pole spans.

### 4. Real-Time Alerting & Edge Autonomy
* Integrated GSM module (SIM800L) dispatches instant SMS alerts and API webhooks directly to field crews.
* **Edge-First Architecture:** Core sensing, local telemetry storage, and anomaly scoring continue locally on ESP32/gateway hardware even during cloud network outages.

---

## 🏗 System Architecture & Workflow

```text
  [ CT / Voltage Sensors ] (Per Segment Node)
             │
             ▼
      [ ESP32 Edge Nodes ]
             │ (ESP-NOW / Wi-Fi Mesh)
             ▼
     [ Local Gateway / Pi ] ───► [ Local Anomaly Score & Verification Engine ]
             │                                       │
             ├───────────────────────────────────────┼──────────────────┐
             ▼                                       ▼                  ▼
     [ Time-Series Store ]                 [ SIM800L GSM Module ]   [ Live Dashboard ]
 (Historical Profile Engine)              (Instant Field SMS)   (Segment Heatmap)
