# 🌾 AgriSentinel

### Edge-AI Powered Wildlife Detection & Selective Bio-Acoustic Deterrence System

AgriSentinel is an **Edge-AI powered real-time wildlife monitoring and deterrence system** designed to protect agricultural fields from crop-destroying wildlife.

The system uses **YOLO26 and OpenCV** to analyze live camera feeds, detect animals in real time, distinguish **threat wildlife from non-threat livestock**, and trigger **species-specific bio-acoustic deterrents** for verified threats.

The project also includes a complete **dataset engineering and model training pipeline**, integrating 6,500+ images from 7 source datasets, standardizing YOLO annotations, training detection models, and evaluating their performance.

---

## 🚀 Key Features

- ⚡ **Real-Time Wildlife Detection** using YOLO26 and OpenCV.
- 🐘 **Multi-Class & Livestock Filtering** for Elephant, Monkey, Wild Boar, Cow, Deer, and Leopard.
- 🎯 **Confidence-Based Threat Detection** using a `0.75` threshold.
- 🔊 **Species-Specific Bio-Acoustic Deterrence** for verified wildlife threats.
- 🧹 **Automated Dataset Engineering** across 6,500+ images from 7 datasets.
- 🤖 **YOLO26 & RT-DETR Training and Benchmarking** with mAP, Precision, Recall, and F1 evaluation.
- 🖥️ **Edge-AI Ready** for low-latency local inference.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| **Language** | Python |
| **Computer Vision** | OpenCV |
| **Object Detection** | YOLO26, RT-DETR |
| **ML Framework** | Ultralytics |
| **Data Processing** | NumPy, OS, Shutil |
| **Audio Processing** | PyGame |
| **Model Evaluation** | mAP@50, Precision, Recall, F1-Score |
| **Version Control** | Git, GitHub |

---

## 📊 Dataset & Model Performance

### Dataset

- **6,500+ images**
- **6 animal classes**
- Combined from **7 source datasets**
- Standardized into **YOLO format**
- Classes: `Elephant`, `Monkey`, `Wild Boar`, `Cow`, `Deer`, `Leopard`

### Model Performance

| Metric | Result |
|---|---:|
| **mAP@50** | **92%** |
| **Confidence Threshold** | **0.75** |
| **Reported False-Alarm Reduction** | **96%** |
| **Reported Response-Time Improvement** | **80%** |

Training and evaluation results for **YOLO26 and RT-DETR** are available in the `runs/detect/` directory.

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
                    │  Frame Acquisition  │
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
                  ┌────────────┴────────────┐
                  │                         │
                  ▼                         ▼
             Non-Threat                 Wildlife
              Livestock                  Threat
                  │                         │
                  ▼                         ▼
               Ignore                Species Mapping
                                            │
                                            ▼
                                  ┌──────────────────┐
                                  │ Bio-Acoustic     │
                                  │ Audio Selection  │
                                  └────────┬─────────┘
                                           │
                                           ▼
                                  🔊 Deterrent Output