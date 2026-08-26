# 🍅 Tomato Disease Classification Benchmark Using Deep Learning

A comprehensive deep learning benchmark framework for automatic tomato leaf disease classification using state-of-the-art CNN architectures with rigorous dataset validation, preprocessing, training protocols, explainable AI, and external generalization evaluation.

---

# 📌 Overview

Plant diseases are a major challenge in agriculture, affecting crop productivity and quality. Early and accurate disease identification can support precision agriculture and reduce economic losses.

This project presents a research-grade benchmark framework for tomato disease classification using deep learning models trained on a carefully validated PlantVillage tomato leaf dataset.

The complete workflow includes:

- Dataset quality verification
- Image integrity checking
- Duplicate removal
- Data leakage prevention
- Exploratory data analysis
- Image preprocessing
- Robust augmentation
- Transfer learning
- CNN architecture benchmarking
- Explainable AI analysis
- External generalization evaluation

---

# 🚀 Research Workflow


Dataset Collection
↓
Dataset Verification
↓
Image Corruption Detection
↓
Duplicate Removal
↓
Exploratory Data Analysis
↓
Clean Dataset Construction
↓
Train/Validation/Test Split
↓
Leakage Verification
↓
Image Preprocessing
↓
Data Augmentation
↓
CNN Benchmark Training
↓
Model Evaluation
↓
Explainable AI
↓
External Validation
↓
Final Analysis


---

# 📂 Dataset

## PlantVillage Tomato Dataset

| Property | Value |
|---|---:|
| Raw Images | 16,011 |
| Exact Duplicates Removed | 14 |
| Final Unique Images | 15,997 |
| Classes | 10 |
| Resolution | 256×256 |
| Format | JPEG |
| Color Mode | RGB |

## Disease Classes


0 Tomato_Bacterial_spot
1 Tomato_Early_blight
2 Tomato_Late_blight
3 Tomato_Leaf_Mold
4 Tomato_Septoria_leaf_spot
5 Tomato_Spider_mites_Two_spotted_spider_mite
6 Tomato__Target_Spot
7 Tomato__Tomato_YellowLeaf__Curl_Virus
8 Tomato__Tomato_mosaic_virus
9 Tomato_healthy


---

# 🔍 Dataset Validation

The dataset undergoes strict quality control.

## Image Integrity

✔ All images scanned  
✔ Corrupted image detection  
✔ 100% valid image coverage  

## Duplicate Detection

### Exact Duplicate Detection

- MD5 hashing
- Duplicate leakage prevention

Result:


Duplicate Groups : 14
Removed Images : 14
Final Images : 15,997


### Near Duplicate Detection

- Perceptual hashing (pHash)
- Cross-split leakage prevention

## Leakage Audit

Verified:


Image ID Overlap : 0
Relative Path Overlap : 0
MD5 Overlap : 0
pHash Split Leakage : 0


---

# 📊 Exploratory Data Analysis

Performed analyses:

- Class distribution
- Image metadata
- Brightness and contrast
- RGB channel statistics
- Sample visualization

Dataset imbalance:


Largest Class:
Yellow Leaf Curl Virus
Images: 3,208

Smallest Class:
Tomato Mosaic Virus
Images: 373

Imbalance Ratio:
8.60 : 1


---

# 🖼 Image Preprocessing

All models follow ImageNet-compatible preprocessing.

Standard models:


Input Size : 224×224
Normalization : ImageNet Mean/Std
Color Space : RGB
Tensor Type : float32


InceptionNet:


Input Size : 299×299


---

# 🔄 Data Augmentation

Training augmentation:

- Random resized crop
- Horizontal flip
- Rotation
- Color variation
- Robust image transformations

Validation/Test:


Deterministic preprocessing only
No augmentation


---

# 🧠 Deep Learning Models

Six ImageNet-pretrained CNN architectures were benchmarked.

| Model | Parameters | Input |
|---|---:|---|
| ResNet50 | 23.5M | 224×224 |
| MobileNetV3-Large | 4.2M | 224×224 |
| EfficientNet-B0 | 4.0M | 224×224 |
| ConvNeXt-Tiny | 27.8M | 224×224 |
| VGG16 | 134.3M | 224×224 |
| InceptionV3 | 21.8M | 299×299 |

---

# ⚙️ Training Configuration

Hardware:


GPU:
NVIDIA GeForce RTX 3050 Laptop GPU

VRAM:
6GB


Framework:


PyTorch
CUDA 12.6
Mixed Precision Training


Optimization:


Optimizer:
AdamW

Learning Rate:
1e-4

Weight Decay:
1e-4

Scheduler:
ReduceLROnPlateau

Maximum Epochs:
30

Early Stopping:
7 epochs

Gradient Clipping:
1.0


---

# 🏋️ Training Strategies

Two experimental settings were evaluated.

## 1. Baseline Training


ImageNet pretrained models

No augmentation

Unweighted Cross Entropy Loss

AdamW optimization


## 2. Improved Training


ImageNet pretrained models

Robust augmentation enabled

Weighted Cross Entropy Loss

Class imbalance handling

AdamW optimization


Validation remained:


Unweighted Cross Entropy Loss


for fair comparison.

---

# 🏆 Baseline Results

Best baseline model:

## 🥇 ConvNeXt-Tiny

| Metric | Score |
|---|---:|
| Validation Loss | 0.006640 |
| Accuracy | 99.83% |

Ranking:

| Rank | Model | Loss | Accuracy |
|---|---|---:|---:|
|1|ConvNeXt-Tiny|0.006640|99.83%|
|2|ResNet50|0.009320|99.79%|
|3|EfficientNet-B0|0.012467|99.75%|
|4|InceptionNet|0.014199|99.62%|
|5|MobileNet|0.021430|99.67%|
|6|VGG16|0.051551|98.96%|

---

# 🏆 Improved Results

Best improved model:

## 🥇 ConvNeXt-Tiny

| Metric | Score |
|---|---:|
| Validation Loss | 0.002713 |
| Accuracy | 99.96% |

Ranking:

| Rank | Model | Loss | Accuracy |
|---|---|---:|---:|
|1|ConvNeXt-Tiny|0.002713|99.96%|
|2|EfficientNet-B0|0.014171|99.58%|
|3|MobileNet|0.014417|99.67%|
|4|ResNet50|0.014729|99.71%|
|5|VGG16|0.040186|99.50%|

---

# 📈 Explainable AI (XAI)

Implemented methods:

- Grad-CAM
- Grad-CAM++
- Attention Rollout
- SHAP

Purpose:

- Visualize disease regions
- Analyze model attention
- Improve interpretability

---

# 🌍 External Evaluation

Future evaluation:

## PlantDoc Dataset

Used for:

- External validation
- Cross-dataset generalization
- Real-world robustness testing

---

# 📁 Project Structure


Tomato_Disease_Research/

├── plantvillage/
├── processed_dataset/
├── splits/
│ ├── train_split.csv
│ ├── validation_split.csv
│ └── test_split.csv
│
├── checkpoints/
│ ├── baseline/
│ └── improved/
│
├── results/
│ ├── eda/
│ ├── preprocessing/
│ ├── augmentation/
│ ├── training/
│ ├── explainability/
│ └── robustness/
│
└── notebooks/


---

# 💻 Installation

```bash
python -m venv tomato_env

tomato_env\Scripts\activate

pip install -r requirements.txt
📦 Requirements
Python 3.12
PyTorch
Torchvision
CUDA
NumPy
Pandas
Scikit-learn
OpenCV
Matplotlib
PIL
tqdm
🔬 Reproducibility

Configuration:

Random Seed:
42

Deterministic Training:
Enabled

CUDA Reproducibility:
Enabled

All dataset splits, preprocessing settings, and training configurations are saved.

📌 Research Contributions

This benchmark provides:

✔ Rigorous dataset cleaning
✔ Leakage-free evaluation
✔ CNN architecture comparison
✔ Class imbalance handling
✔ Robust augmentation analysis
✔ Transfer learning benchmark
✔ Explainable AI evaluation
✔ External generalization framework

👨‍💻 Author

Deep Learning Research Project

Tomato Disease Classification Benchmark

📜 License

This project is intended for academic research and educational purposes.