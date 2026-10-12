# SignSync 🖐️💬
### Bridging Voices, On-Device

[![Status](https://img.shields.io/badge/Status-Prototype-orange?style=for-the-badge)]()
[![Platform](https://img.shields.io/badge/Platform-Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)]()
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)]()



**SignSync** is a private, offline, real-time Indian Sign Language (ISL) translator that runs entirely on a smartphone. No cloud. No upload. No compromise.

Over **2.78 million** hearing-impaired Indians rely on ISL for communication — yet every existing translation tool is cloud-dependent, requires stable internet, and uploads camera and mic data. SignSync closes that gap by running a full AI cascade on-device.

**We’re not building a demo. We’re building the first ISL translator that respects the user’s privacy.**

---

##  Core Innovations

- **Fully On-Device** — Vision, speech, and language models all run on the Snapdragon NPU. Zero bytes leave the phone.
- **Bidirectional** — ISL → Text/Speech **and** Speech → Animated ISL avatar.
- **Modular Cascade** — Five models, each testable in isolation. Ship vision → text on Day 1, add speech later.
- **Sub-400ms Latency** — No round trip to a server. Conversation feels natural, not stilted.

---

## 📊 Why This Matters

| Requirement | Cloud App | Typical On-Device | **SignSync** |
|---|---|---|---|
| Works without internet | ❌ No | ⚠️ Partial | ✅ **Yes** |
| Data leaves device | ❌ Always | ⚠️ Sometimes | ✅ **Never** |
| Latency | 1–3 s | 200–800 ms | ✅ **< 400 ms** |
| Bidirectional ISL | Rare | No | ✅ **Yes** |
| Runs on phone NPU | No | Partial | ✅ **Fully** |
| Usable in hospitals | ❌ No | ⚠️ Maybe | ✅ **Yes** |

---

##  Architecture (at a glance)

amera → MediaPipe → LSTM → Gemma 2B → Piper TTS
Mic → Whisper → Gemma 2B → Signing Avatar


**Every model runs on the Snapdragon NPU. Nothing leaves the phone.**

---

##  On-Device AI Stack

| Layer | Model / Tool | Why |
|---|---|---|
| Vision | MediaPipe Holistic | Real-time hand + body landmarks, no GPU needed |
| Classification | Quantized LSTM (TFLite / ONNX) | Small enough for NPU, accurate on ISL sequences |
| Speech in | Whisper Tiny | Offline STT, robust to Indian accents |
| Speech out | Piper TTS | Natural voice, runs fully offline |
| Language | Gemma 2B / Phi-3, 4-bit | Grammar refinement + ISL gloss generation |
| Runtime | ONNX Runtime + NNAPI | Snapdragon NPU acceleration, no cloud calls |

**Stack:** Kotlin · Jetpack Compose · TFLite · MediaPipe · llama.cpp · ONNX Runtime

