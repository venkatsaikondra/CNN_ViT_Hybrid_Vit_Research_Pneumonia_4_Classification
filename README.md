# 🫁 Pneumonia 4-Class Classification: CNN vs ViT vs Hybrid-ViT

> A systematic comparative study of Convolutional Neural Networks, Vision Transformers, and a Hybrid-ViT architecture on balanced, separately-augmented chest X-ray data for multi-class pneumonia detection.

---

## 📌 Overview

Pneumonia remains a leading cause of mortality worldwide, and accurate automated classification from chest X-rays is a clinically valuable task. This research benchmarks three deep learning architectures — **CNN**, **ViT (Vision Transformer)**, and a **Hybrid-ViT** — on a **4-class pneumonia classification** problem:

| Class | Description |
|-------|-------------|
| `Normal` | Healthy chest X-ray |
| `Viral Pneumonia` | Pneumonia caused by viral infection |
| `Bacterial Pneumonia` | Pneumonia caused by bacterial infection |
| `COVID-19 Pneumonia` | Pneumonia associated with SARS-CoV-2 |

A key methodological contribution is the use of **class-balanced datasets with class-wise separate augmentation**, ensuring no data leakage between augmented splits and a fair comparison across architectures.

---

## 🧪 Research Highlights

- **Equal-sample balancing** across all 4 classes to eliminate class imbalance bias
- **Separate augmentation pipelines** for each class — augmentation is applied independently per class before the train/test split, preventing any form of data leakage
- Three architectures trained and evaluated under identical conditions
- Full confusion matrices provided for each model
- Results analyzed in `Analysis.xlsx`

---

## 🗂️ Repository Structure

```
CNN_ViT_Hybrid_ViT_Research_Pneumonia_4_Classification/
│
├── Data_Collection/              # Raw dataset collection scripts & sources
├── Unique_Raw/                   # Deduplicated raw X-ray images
├── Raw/                          # Original raw images per class
│
├── Equal_sample/                 # Class-balanced subset (equal N per class)
│
├── Data_Augmentation/            # Augmentation scripts (applied per class separately)
│
├── CNN_Augmented_Data/           # Augmented data prepared for CNN training
├── Vit_Augmented_Data/           # Augmented data prepared for ViT training
│
├── Train_Test_Split_CNN_Data/    # Final train/test splits for CNN
├── Train_Test_Split_Vit_Data/    # Final train/test splits for ViT & Hybrid-ViT
│
├── CNN/                          # CNN model — architecture, training, evaluation
├── ViT/                          # Vision Transformer — architecture, training, evaluation
├── Hybrid_Vit/                   # Hybrid-ViT — CNN feature extractor + ViT encoder
│
├── Analysis.xlsx                 # Consolidated metrics comparison across all models
└── README.md
```

---

## 🔄 Data Pipeline

The data pipeline is designed to be reproducible and bias-free:

```
Raw X-rays
    ↓
Deduplication (Unique_Raw)
    ↓
Class Balancing — Equal samples per class (Equal_sample)
    ↓
Per-Class Augmentation (Data_Augmentation)
    ↓                          ↓
CNN_Augmented_Data      Vit_Augmented_Data
    ↓                          ↓
Train/Test Split        Train/Test Split
(CNN)                   (ViT / Hybrid-ViT)
    ↓                          ↓
CNN Training          ViT / Hybrid-ViT Training
```

> ⚠️ **Important:** Augmentation is performed **before** splitting, but applied **per class independently**, ensuring class distributions are preserved and no augmented sample from the test set contaminates training.

---

## 🏗️ Model Architectures

### 1. CNN (Convolutional Neural Network)
A custom CNN built for spatial feature extraction from chest X-rays. Uses stacked convolution + pooling blocks followed by fully connected classification layers.

### 2. ViT (Vision Transformer)
Implements the standard ViT architecture — images are divided into fixed-size patches, linearly embedded, and passed through a Transformer encoder with multi-head self-attention. Captures global dependencies across the entire image.

### 3. Hybrid-ViT
Combines the strengths of both: a **CNN backbone extracts local spatial features**, which are then fed as patch tokens into a **ViT encoder**. This hybrid approach is designed to benefit from both local feature extraction (CNN) and global context modeling (ViT).

---

## 📊 Confusion Matrices

Confusion matrices are provided for each model to show per-class performance:

### CNN — Confusion Matrix
![CNN Confusion Matrix](assets/confusion_matrix_cnn.png)

### ViT — Confusion Matrix
![ViT Confusion Matrix](assets/confusion_matrix_vit.png)

### Hybrid-ViT — Confusion Matrix
![Hybrid-ViT Confusion Matrix](assets/confusion_matrix_hybrid_vit.png)

> 📁 Place your confusion matrix images in an `assets/` folder and name them as shown above, or update the paths to match your file names.

---

## 📈 Results Summary

Full metrics are available in [`Analysis.xlsx`](./Analysis.xlsx).

| Model | Accuracy | Precision | Recall | F1-Score |
|------------|----------|-----------|--------|----------|
| CNN | — | — | — | — |
| ViT | — | — | — | — |
| Hybrid-ViT | — | — | — | — |

> 📝 Fill in your final numbers from `Analysis.xlsx`.

---

## ⚙️ Setup & Requirements

### Environment

```bash
Python >= 3.8
PyTorch >= 1.12  (or TensorFlow if applicable)
torchvision
timm              # for ViT models
numpy
pandas
matplotlib
seaborn
scikit-learn
Pillow
tqdm
openpyxl
```

### Install dependencies

```bash
pip install torch torchvision timm numpy pandas matplotlib seaborn scikit-learn pillow tqdm openpyxl
```

---

## 🚀 How to Run

### Step 1 — Data Preparation
```bash
# Collect and deduplicate data
cd Data_Collection && python collect.py

# Balance classes
cd ../Equal_sample && python balance.py

# Augment per class
cd ../Data_Augmentation && python augment.py
```

### Step 2 — Train/Test Split
```bash
cd Train_Test_Split_CNN_Data && python split.py
cd ../Train_Test_Split_Vit_Data && python split.py
```

### Step 3 — Train Models
```bash
# CNN
cd ../CNN && python train.py

# ViT
cd ../ViT && python train.py

# Hybrid-ViT
cd ../Hybrid_Vit && python train.py
```

### Step 4 — Evaluate
Each model folder contains an `evaluate.py` (or equivalent notebook) that generates confusion matrices and metrics.

---

## 🧬 Dataset

The dataset is sourced from publicly available chest X-ray repositories (e.g., Kaggle Chest X-Ray datasets, COVID-19 radiography databases). Images were deduplicated and then balanced to an equal number of samples per class before augmentation.

**Classes:** Normal · Viral Pneumonia · Bacterial Pneumonia · COVID-19 Pneumonia

---

## 📄 Citation

If you use this work or find it useful, please cite:

```bibtex
@misc{venkatsaikondra2025pneumonia,
  author       = {Venkat Sai Kondra},
  title        = {CNN vs ViT vs Hybrid-ViT: A Comparative Study on 4-Class Pneumonia Classification with Balanced and Separately Augmented Chest X-Ray Data},
  year         = {2025},
  howpublished = {\url{https://github.com/venkatsaikondra/CNN_ViT_Hybrid_Vit_Research_Pneumonia_4_Classification}},
}
```

---

## 👤 Author

**Venkat Sai Kondra**
[GitHub](https://github.com/venkatsaikondra)

---

## 📜 License

This project is intended for research and educational purposes. Please refer to the original dataset licenses for data usage terms.
