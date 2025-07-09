# MURA Fracture Detection using Deep Learning

Automated fracture detection from musculoskeletal radiographs using deep learning. This project explores multiple neural network architectures — including a custom CNN, ResNet50, DenseNet169, and EfficientNet-B0 — trained and evaluated on the [MURA dataset](https://stanfordmlgroup.github.io/competitions/mura/). Body part classification is incorporated as an auxiliary task to improve fracture detection through contextual information.

---

##  Project Overview

- **Primary Task**: Binary classification — Fracture vs. No Fracture  
- **Secondary Task**: Body Part Classification (Elbow, Finger, Forearm, Hand, Humerus, Shoulder, Wrist)  
- **Approach**: Multi-task deep learning using grayscale X-ray images  
- **Framework**: [PyTorch](https://pytorch.org/)

---

##  Dataset

### 1. [MURA (Musculoskeletal Radiographs)](https://stanfordmlgroup.github.io/competitions/mura/)
- One of the largest public datasets of musculoskeletal radiographs.
- Contains 40,000+ images from 7 upper extremity body parts.
- Each image is labeled as **positive (fractured)** or **negative (non-fractured)**.

### 2. [External Dataset for Generalization](https://www.kaggle.com/datasets/bmadushanirodrigo/fracture-multi-region-x-ray-data)
- Used to test cross-domain generalization.
- Contains fracture X-rays from different clinical sources.

---

## Model Architectures

| Model         | Pretrained | Multi-task | Best Accuracy | ROC AUC |
|---------------|------------|------------|----------------|----------|
| Custom CNN    | ❌         | ❌         | 66.28%         | 0.7272   |
| ResNet50      | ✅         | ✅         | 75.07%         | 0.8237   |
| DenseNet169   | ✅         | ✅         | 79.20%         | 0.8541   |
| EfficientNetB0| ✅         | ✅         | **80.64%**     | **0.8710** |

All pretrained models are adapted to accept grayscale (1-channel) inputs.

---

##  Results

- **Multi-task learning** significantly improved fracture classification performance.
- **EfficientNet-B0** achieved the best accuracy and ROC AUC.
- External dataset testing showed good generalization (76% accuracy).
- Body part classification provided meaningful anatomical context.

---

## How to Run
## How to Run

1. **Clone this repository** and upload it to [Google Colab](https://colab.research.google.com/).
2. **Download the MURA dataset** from the [official Stanford MURA site](https://stanfordmlgroup.github.io/competitions/mura/) after signing the required agreement.
   - Place the `valid_image_paths.csv` and the image folders (e.g., `MURA-v1.1/train/`, `MURA-v1.1/valid/`) in your **Google Drive**.
3. *(Optional)* **Download the external dataset** for generalization testing from [this Kaggle challenge](https://www.kaggle.com/datasets/bmadushanirodrigo/fracture-multi-region-x-ray-data).
4. **Mount your Google Drive** in Colab using the following code:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
5. Update file paths in the notebook cells to point to your Google Drive locations.
6. Run the desired notebook to train models and generate predictions.

---

##  Project Structure

```bash
.
├── code/
│ ├── Custom_CNN.ipynb
│ ├── ResNet50.ipynb
│ └── EfficientNet_&_DenseNet.ipynb
├── README.md
```

## Acknowledgments

This project was completed as part of the MSc course on Deep Learning at Athens University of Economics and Business (AUEB).  
Special thanks to Professor Themos Stafylakis for their valuable guidance throughout the project.

