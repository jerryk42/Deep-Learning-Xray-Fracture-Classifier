# MURA Fracture Detection using Deep Learning

Automated fracture detection from musculoskeletal radiographs using deep learning. This project explores multiple neural network architectures — including a custom CNN, ResNet50, DenseNet169, and EfficientNet-B0 — trained and evaluated on the [MURA dataset](https://stanfordmlgroup.github.io/competitions/mura/). Body part classification is incorporated as an auxiliary task to improve fracture detection through contextual information.

---

## 🧠 Project Overview

- **Primary Task**: Binary classification — Fracture vs. No Fracture  
- **Secondary Task**: Body Part Classification (Elbow, Finger, Forearm, Hand, Humerus, Shoulder, Wrist)  
- **Approach**: Multi-task deep learning using grayscale X-ray images  
- **Framework**: [PyTorch](https://pytorch.org/)

---

## 📁 Dataset

### 1. [MURA (Musculoskeletal Radiographs)](https://stanfordmlgroup.github.io/competitions/mura/)
- One of the largest public datasets of musculoskeletal radiographs.
- Contains 40,000+ images from 7 upper extremity body parts.
- Each image is labeled as **positive (fractured)** or **negative (non-fractured)**.

### 2. [External Dataset for Generalization](https://www.kaggle.com/datasets/bmadushanirodrigo/fracture-multi-region-x-ray-data)
- Used to test cross-domain generalization.
- Contains fracture X-rays from different clinical sources.

---

## 🏗️ Model Architectures

| Model         | Pretrained | Multi-task | Best Accuracy | ROC AUC |
|---------------|------------|------------|----------------|----------|
| Custom CNN    | ❌         | ❌         | 66.28%         | 0.7272   |
| ResNet50      | ✅         | ✅         | 75.07%         | 0.8237   |
| DenseNet169   | ✅         | ✅         | 79.20%         | 0.8541   |
| EfficientNetB0| ✅         | ✅         | **80.64%**     | **0.8710** |

All pretrained models are adapted to accept grayscale (1-channel) inputs.

---

## 📊 Results

- **Multi-task learning** significantly improved fracture classification performance.
- **EfficientNet-B0** achieved the best accuracy and ROC AUC.
- External dataset testing showed good generalization (76% accuracy).
- Body part classification provided meaningful anatomical context.

---

## 📂 Project Structure

```bash
.
├── data/                   # Processed MURA dataset and external X-rays
├── models/                 # Model definitions (CNN, ResNet, etc.)
├── utils/                  # Helper functions (visualization, metrics, etc.)
├── outputs/                # Saved plots, architecture diagrams, confusion matrices
├── results/                # Evaluation tables, classification reports
├── train.py                # Training script
├── evaluate.py             # Evaluation and metrics
├── README.md               # Project documentation
