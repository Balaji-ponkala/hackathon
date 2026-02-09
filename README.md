# 🧠 Wafer Defect Detection using Deep Learning

## 📌 Overview
This project focuses on automated defect detection in silicon wafer images using deep learning and transfer learning.  
The objective is to classify wafer images into:
- **Normal (No defect)**
- **Defective (Any type of defect)**

This work is submitted as part of a **hackathon Phase-1 submission**, emphasizing dataset preparation, model development, evaluation, and reproducibility.

---


---

## 📊 Dataset Description

The project uses the **WM-811K Wafer Map Dataset**, a publicly available and widely used dataset for wafer defect analysis.

### Dataset Sources
- https://www.kaggle.com/datasets/muhammedjunayed/wm811k-silicon-wafer-map-dataset-image  
- https://www.kaggle.com/datasets/qingyi/wm811k-wafer-map  

### Class Definition
- **Normal** → `none` category in the dataset
- **Defect** → All defect categories merged into a single class

This converts the problem into **binary classification**, suitable for Phase-1.

---

## 🧪 Data Preparation & Splitting

The dataset is automatically downloaded using `kagglehub` and restructured into:


### Split Ratio
- Training: 70%
- Validation: 15%
- Testing: 15%

---

## 🔧 Preprocessing & Augmentation

### Training Data
- Resize to 224×224
- Random horizontal flip
- Random rotation (±15°)
- Brightness and contrast jitter
- Normalization to [-1, 1]

### Validation & Test Data
- Resize and normalization only  
(No augmentation to ensure unbiased evaluation)

---

## 🧠 Model Architecture

- **Backbone**: ResNet-18 (pretrained on ImageNet)
- **Approach**: Transfer learning with frozen backbone

### Custom Classifier Head


Linear → ReLU → Dropout → Linear (2 classes)


This design balances **low bias** and **low variance**.

---

## ⚙️ Training Details

- Loss Function: Cross-Entropy Loss
- Optimizer: Adam
- Batch Size: 32
- Epochs: 10
- Best model saved based on validation accuracy

---

## 📈 Evaluation Results

- **Test Accuracy**: ~89%

### Observations
- Strong performance on defective wafers
- Lower recall for normal wafers due to class imbalance  
  (Acknowledged and planned for improvement)

---

## 🔍 Inference on New Images

```python
label, confidence = predict_new_image("path/to/image.png")
print(label, confidence)
Clone the repository
git clone https://github.com/your-username/wafer-defect-detection.git
cd wafer-defect-detection

2. Install dependencies
pip install -r requirements.txt

3. Run the notebook

Open and run:

notebook/wafer_defect_training.ipynb
