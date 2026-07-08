<div align="center">

# 🚨 Smart Incident Detection System
### Real-Time Multimodal Edge AI for Safety-Critical Environments

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Seeed%20XIAO%20ESP32S3-green)](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/)
[![AI Model](https://img.shields.io/badge/AI-GPT--4o%20Vision-orange)](https://openai.com/)
[![Backend](https://img.shields.io/badge/Backend-Python%20%7C%20Flask%20%7C%20Socket.IO-yellow)](https://flask.palletsprojects.com/)
[![Award](https://img.shields.io/badge/GradinnoHack%202025-Winner-gold)](https://github.com/Perumallasrinu/Hackthon-2025/blob/main/hackthon_certificate.pdf)

**🏆 GradinnoHack 2025 Winner — Team Reboot Rebels**

*An autonomous, AI-powered surveillance system that detects emergencies in real time using edge-deployed vision and a multimodal LLM pipeline — eliminating manual monitoring and enabling sub-5-second first responder dispatch.*

</div>

---

## 📊 Performance Metrics

| Metric | Result |
|--------|--------|
| Emergency Classification Accuracy | **~85%** (zero-shot, on-device) |
| Average Incident Detection Latency | **< 5 seconds** end-to-end |
| Edge Compute Platform | Seeed XIAO ESP32S3 (low-power, < 1W) |
| Communication Security | SSL/TLS encrypted edge-to-server |
| Concurrent Access Testing | Token-auth stress-tested |
| Detected Incident Types | Fire · Robbery · Accident · Flooding |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        EDGE LAYER                                   │
│  ┌──────────────────────────────────────┐                           │
│  │   Seeed XIAO ESP32S3 (CCTV Node)    │                           │
│  │  ┌──────────┐    ┌───────────────┐  │                           │
│  │  │  Camera  │───▶│ Edge Impulse  │  │  SSL/TLS encrypted        │
│  │  │  Module  │    │  (Inference)  │  │─────────────────────────▶ │
│  │  └──────────┘    └───────────────┘  │                           │
│  └──────────────────────────────────────┘                           │
└─────────────────────────────────────────────────────────────────────┘
                              │
                    Triggers Image + Location
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      BACKEND SERVER                                 │
│                                                                     │
│  ┌─────────────┐    ┌────────────────┐    ┌───────────────────┐    │
│  │   Prompt    │───▶│  GPT-4o Vision │───▶│   PushBullet      │    │
│  │  (Context)  │    │  Multimodal LLM│    │   (Alerting)      │    │
│  └─────────────┘    └────────────────┘    └───────────────────┘    │
│                              │                      │              │
│                              ▼                      ▼              │
│                     ┌──────────────┐    ┌───────────────────┐     │
│                     │   MongoDB    │    │    Socket.IO       │     │
│                     │  (Database)  │    │  (Real-time WS)   │     │
│                     └──────────────┘    └───────────────────┘     │
└─────────────────────────────────────────────────────────────────────┘
                              │
                      Push Notification Service
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────────┐
│                      FRONT-END / DISPATCH                           │
│           ReactJS Dashboard  ·  PushBullet App  ·  REST API         │
│               ── Real-time alerts to First Responders ──            │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🔍 Problem Statement

Traditional CCTV surveillance relies on **manual human monitoring** — slow, error-prone, and unscalable. In smart city environments, emergencies like fires, accidents, and crimes can go undetected for critical minutes.

**This system replaces manual monitoring with an always-on, AI-driven pipeline that detects, classifies, and dispatches alerts automatically — in under 5 seconds.**

---

## 🛠️ Tech Stack

### Hardware
| Component | Role |
|-----------|------|
| **Seeed XIAO ESP32S3** | Edge camera node — low-power, compact MCU with integrated camera |

### Software
| Layer | Technology |
|-------|------------|
| **Edge Inference** | Edge Impulse (on-device image classification) |
| **AI / Vision LLM** | GPT-4o Vision (multimodal incident classification) |
| **Backend** | Python · Flask · Socket.IO · PushBullet |
| **Database** | MongoDB (image, context, label, timestamp storage) |
| **Frontend** | ReactJS · Node.js (live notification dashboard) |
| **Dispatch** | REST APIs · WebSocket (real-time bidirectional comms) |
| **Communication** | SSL/TLS (edge-to-server) · WebSocket |

---

## 🔒 Security Architecture

The system is hardened against common attack vectors at every layer:

**Authentication & Access Control**
- Token-based authorization with rate limiting on all API endpoints
- Hashed password storage with secure verification
- Content Security Policy (CSP) headers — XSS and CSRF mitigation

**Communication Security**
- SSL/TLS encryption for all ESP32 ↔ Server communication
- WebSocket secured for real-time bidirectional data streams

**Future Hardening (Roadmap)**
- Web Application Firewall (WAF) — blocks malicious traffic, request type restrictions
- Network Firewall + IDS — IP/port whitelisting, malware detection, access audit logs

---

## 🚀 How It Works

1. **Capture** — Seeed XIAO ESP32S3 continuously captures visual frames via the onboard camera module
2. **Infer at Edge** — Edge Impulse runs on-device inference to detect motion/anomaly triggers (< 1W power)
3. **Classify** — Triggered frames are sent over SSL/TLS to the backend, where GPT-4o Vision analyzes the scene and extracts incident-related keywords
4. **Decide** — The LLM classifies the event: `emergency` or `non-emergency`, with keyword context (fire, accident, flooding, robbery)
5. **Dispatch** — PushBullet and Socket.IO push real-time alerts to first responders via web dashboard and mobile app, with location metadata

---

## 📸 Live Notification Demo

> **Emergency detected at Discovery Park K150**
> Keywords: `accident` · `emergency` · `fire` · `damage` · `vehicle`
> Decision: 🔴 **EMERGENCY**

*Real-time push notification dispatched to first responders in < 5 seconds.*

---

## 📁 Repository Structure

```
Hackthon-2025/
├── smartincidentdetection-main/    # Core application source code
│   ├── backend/                    # Python Flask server + LLM pipeline
│   ├── frontend/                   # ReactJS dashboard
│   └── embedded/                   # ESP32S3 firmware (C/C++)
├── Smart-Incident-Detection-System_...pptx   # Full project presentation
├── reebot-rebels_hackthon_2025.pdf           # Technical report
├── hackthon_certificate.pdf                  # GradinnoHack 2025 award certificate
├── system-architeture.jpg                    # System architecture diagram
├── Picture1.jpg                              # Live notification screenshot
├── Picture2.jpg                              # Architecture diagram
├── demo.mp4                                  # Live system demo video
└── 3D Printing.zip                           # 3D-printed enclosure design files
```

---

## 🎯 Impact & Applications

| Domain | Application |
|--------|-------------|
| **Smart Cities** | Autonomous public safety monitoring across urban infrastructure |
| **First Responder Dispatch** | Sub-5-second alert delivery to emergency services |
| **Critical Infrastructure** | Scalable across campus, transit, and industrial environments |
| **Edge AI / IoT** | Demonstrates production-viable LLM inference pipeline on low-power hardware |

---

## 🔮 Future Roadmap

- [ ] Audio stream analysis (gunshot, glass break, siren detection)
- [ ] Real-time 911 CAD (Computer-Aided Dispatch) API integration
- [ ] Expand AI command center dashboard for multi-node management
- [ ] Optimize TFLite Micro models for full on-device ESP32S3 inference
- [ ] WAF deployment for production-grade API security
- [ ] Multi-camera mesh network with BLE/LoRa coordination

---

## 👥 Team — Reboot Rebels

| Name | Degree |
|------|--------|
| **Srinu Perumalla** | MS, Computer Engineering — University of North Texas |
| Deepak Kumar Sampanthkumar | MS, Computer Science — UNT |
| Harshavardhan Sasikumar | MS, Computer Science — UNT |
| Chaithanya Chowdhary Enugu | MS, Computer Science — UNT |
| Praveen Kumar Deshamone | MS, Cybersecurity — UNT |

---

## 🏆 Award

**GradinnoHack 2025 — Winner**
*Category: AI for Social Good · IoT/Embedded Systems · Public Safety/Crisis Response*

[View Certificate →](./hackthon_certificate.pdf)

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

<div align="center">

**Built at GradinnoHack 2025 · University of North Texas**

*"Faster detection. Safer communities. Smarter cities."*

</div>
