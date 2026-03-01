# Performance Analysis of YOLO11 and YOLO26 with SAHI for Weed Seed Identification

![Python](https://img.shields.io/badge/python-3.12-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.1-red.svg)
![Ultralytics](https://img.shields.io/badge/Ultralytics-8.4-yellow.svg)

This repository contains the performance metrics and evaluation results for a comparative study between **YOLO11** and **YOLO26** architectures, enhanced with **Slicing Aided Hyper Inference (SAHI)**.

The primary objective of this research is the automated **detection, classification, and quantification** of high-impact, small-seeded weed species (*Amaranthus palmeri*, *Amaranthus tuberculatus*, and *Bassia scoparia*).

> **⚠️ Confidentiality Notice:** Raw datasets, original images, and model weights (`.pt` files) are currently restricted to protect research integrity prior to formal publication. This repository serves as a record of validation metrics and performance logs.

---

## 🔬 Research Overview

Manual quantification of weed seeds is a labor-intensive bottleneck in weed science. This project leverages state-of-the-art computer vision to automate the identification of minute specimens ($< 2$ mm).

### Technical Stack
* **Architectures:** Ultralytics YOLO11n & YOLO26n (NMS-free).
* **Optimization:** Slicing Aided Hyper Inference (SAHI) to resolve small-object spatial loss.
* **Hardware:** NVIDIA RTX PRO 6000 Blackwell Server Edition.
* **Dataset:** 2,250 manually annotated seeds (80/20 train/test split).
* **Environment:** Varying light conditions and backgrounds (white paper, black tabletop, tissue).

---

## 📊 Performance Metrics

Detailed metrics were generated using a shared COCO-format ground truth (`test_coco_matched.json`) to ensure parity between models.

### Overall Validation
| Metric | YOLO11 | YOLO26 |
| :--- | :---: | :---: |
| **mAP50** | 97.5% | **98.6%** |
| **mAP50-95** | 68.2% | **74.3%** |
| **F1-Score** | 0.941 | **0.956** |

### Small Object Detection ($AP_{small}$) with SAHI
| Metric | YOLO11 + SAHI | YOLO26 + SAHI | Improvement |
| :--- | :---: | :---: | :---: |
| **Average Precision ($AP_s$)** | 53.0% | **74.0%** | **+21.0%** |
| **Average Recall ($AR_s$)** | 70.2% | **75.8%** | **+5.6%** |

---

## 📈 Key Insights

1. **Architecture Efficacy:** The NMS-free architecture of **YOLO26** demonstrated superior localization for micro-objects, significantly outperforming YOLO11 in $AP_s$.
2. **SAHI Implementation:** Standard inference resolution (1280px) struggled with feature loss for seeds under 2mm. SAHI slicing effectively preserved these features, allowing for high-sensitivity detection.
3. **Hardware Acceleration:** Utilizing the **Blackwell GPU** architecture allowed for rapid 300-epoch training and high-throughput inference, making the system viable for large-scale seedbank analysis.

---

## 📂 Repository Structure
```text
├── metrics/
│   ├── YOLO11_Final/          # Confusion matrices, P-curves, F1-curves
│   └── YOLO26_Final/          # Validation results for YOLO26
├── SAHI_Eval/                 # Exported COCO-format result.json files
└── README.md

```
---

## 🎓 Author

**Ashish Chaudhary** *PhD Student | Biological Sciences (Plant Science)* South Dakota State University  
Department of Agronomy, Horticulture, and Plant Science  

**Advisor:** Dr. Sachin Dhanda

---

## ✉️ Contact & Networking

I am actively exploring new research collaborations and lab opportunities starting Summer 2026. Feel free to reach out via the following platforms:

* **LinkedIn:** [linkedin.com/in/ashish-chaudhary](https://www.linkedin.com/in/ashish-chaudhary-89b231285/)
* **Email:** [ashish.chaudhary@sdstate.edu](mailto:ashish.chaudhary@sdstate.edu)
* **Portfolio:** [LearnWithAshish2 (YouTube)](https://www.youtube.com/@LearnWithAshish2)

---

## ⚖️ License

The performance data and metrics provided in this repository are intended for academic review and transparency. 

**All rights reserved.** All underlying research methodology, original image datasets, and trained model weights are the intellectual property of the author and the **Department of Agronomy, Horticulture, and Plant Science at South Dakota State University**. No part of the proprietary methodology or data may be reproduced or used without explicit permission until formal publication.

Copyright (c) 2026 Ashish Chaudhary

