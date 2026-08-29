# 🌾 AgriSentinel

### Edge-AI Powered Wildlife Detection & Selective Bio-Acoustic Deterrence System

AgriSentinel is an **Edge-AI powered real-time wildlife monitoring and deterrence system** designed to protect agricultural fields from crop-destroying wildlife.

The system uses **YOLO26 and OpenCV** to analyze live camera feeds, detect animals in real time, filter detections using confidence-based decision logic, distinguish **threat wildlife from non-threat livestock**, and trigger **species-specific bio-acoustic deterrents** for verified threats.

The project also includes a complete **dataset engineering and model training pipeline**, including the integration of 6,500+ images from multiple datasets, YOLO-format annotation standardization, model training, evaluation, and benchmarking against RT-DETR.

---

## 🏗️ System Architecture

```text
                        ┌─────────────────────┐
                        │   CCTV / Webcam     │
                        └──────────┬──────────┘
                                   │
                                   ▼
                        ┌─────────────────────┐
                        │   OpenCV Pipeline   │
                        │ Frame Acquisition   │
                        └──────────┬──────────┘
                                   │
                                   ▼
                        ┌─────────────────────┐
                        │      YOLO26         │
                        │   Object Detection  │
                        └──────────┬──────────┘
                                   │
                                   ▼
                        ┌─────────────────────┐
                        │ Confidence Filter   │
                        │      ≥ 0.75         │
                        └──────────┬──────────┘
                                   │
                                   ▼
                        ┌─────────────────────┐
                        │ Species Detection   │
                        └──────────┬──────────┘
                                   │
                     ┌─────────────┴─────────────┐
                     │                           │
                     ▼                           ▼
               Non-Threat                    Wildlife
                Livestock                     Threat
                     │                           │
                     ▼                           ▼
                  Ignore                 Species Mapping
                                                 │
                                                 ▼
                                      ┌──────────────────┐
                                      │ Bio-Acoustic     │
                                      │ Audio Selection  │
                                      └────────┬─────────┘
                                               │
                                               ▼
                                      🔊 Deterrent Output