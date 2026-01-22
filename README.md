# Basketball Shot Category Recognition Using Wearable Sensors and Feature-Based Machine Learning

This repository contains the end-to-end machine learning pipeline for classifying basketball shots (Paint, Free-Throw, and 3-Point) using multi-modal sensor data from wrist-worn IMUs.

# Project Overview

Traditional basketball analytics rely on expensive vision-based systems or subjective coaching. This project proposes a **low-cost, high-accuracy alternative** using smartphone inertial sensors. By transforming raw local-frame acceleration into a global earth-frame, the system isolates vertical lift energy to recognize shooting patterns across diverse participants.

# Data Collection & Specification

* **Participants:** 11 unique subjects (8 males, 3 females).
* **Anthropometric Range:** Height 159cm to 196cm.
* **Data Volume:** 330 total shots (10 shots per category per participant).
* **Shot Categories:** 1.**The Paint:** Short-range proximity shots. 2.**Free-Throw:** Mid-range standardized foul shots. 3.**3-Point Zone:** Long-range high-arc shots.
* **Hardware:** Accelerometer, Gyroscope, Gravity, and Orientation sensors captured at variable frequencies (~53Hz).

# Methodology Summary

# **1. Preprocessing & Signal Alignment**

* **Linear Interpolation:** Resamples variable sensor streams to a synchronized **50Hz** frequency.
* **Coordinate Transformation:** Implements a quaternion-based rotation to align sensor data to a global Earth-fixed frame, ensuring rotation-invariant acceleration magnitude.

# **2. Adaptive Segmentation**

* **Physics-Driven Logic:** Uses peak detection (>11.5 ) and a dynamic 2-second window.
* **Biometric Calibration:** Thresholds are dynamically adjusted based on participant height and gender to account for varying explosive power.

# **3. Feature Engineering (200+ Features)**

* **Time-Domain:** Statistical markers including Mean, Std, Skewness, and Kurtosis.
* **Frequency-Domain:** FFT dominant frequencies and spectral energy.
* **Biomechanical Features:** Includes **Effort Ratio** (normalized force), **Jerk** (motion smoothness), and estimated release angles.

# **4. The Classifier Tournament**

To ensure optimal performance, a competitive benchmark was executed across nine distinct architectures:

* K-Nearest Neighbors (KNN)
* Logistic Regression
* Decision Tree
* **Support Vector Classifier (SVC)** — **Winner**
* CatBoost & XGBoost
* LightGBM (LGBM)
* Random Forest
* Multi-Layer Perceptron (Neural Networks)

---

# Results & Evaluation

* **Top Accuracy:** **94.5%** achieved by the optimized SVC.
* **Performance Metric:** The model selection was prioritized based on **F1-Score** to ensure balanced recognition across all three shot zones.
* **Real-Time Readiness:** Inference latency benchmarks confirm the pipeline is suitable for real-time mobile application feedback.

---

# Repository Structure

```text
├── data/                   # Raw sensor logs for Subjects 1-11 (.zip)
├── notebooks/              # Comprehensive experimental pipeline
│   └── Basketball_Shot_Classification.ipynb
├── docs/                   # Research paper, LaTeX sources, and diagrams
│   └── Nouran Diagram.pdf                
└── README.md


# Authors

**Nouran El-Salmawy, Sohaila Abdelwahab, and Hagar Mahgoub** *Students, Department of Electronics and Communication Engineering* *Arab Academy for Science, Technology and Maritime Transport*

# License

This project is licensed under the MIT License - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

# **Citation**

If you use this work in your research, please cite:

> *N. El-Salmawy, S. Abdelwahab, and H. Mahgoub, "Basketball Shot Category Recognition Using Wearable Sensors and Feature-Based Machine Learning," (Under Review, 2024).*
