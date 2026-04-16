
---

# Automated Diabetic Retinopathy Severity Grading

### Deep Learning Pipeline using ResNet-50 vs DenseNet-121

## Overview

This project presents an end-to-end deep learning pipeline for **automated diabetic retinopathy (DR) severity grading** using retinal fundus images. The system predicts clinically relevant DR stages (0–4) and is designed to support **scalable and reliable medical screening**.

We compare two approaches:

* **ResNet-50** → Multi-class classification baseline
* **DenseNet-121** → Ordinal regression model (proposed)

The focus is on **clinical reliability**, emphasizing:

* Reduction of severe misclassification errors
* Improved detection of **referable DR (grades 2–4)**
* Efficient and scalable model design

---

## Key Features

* End-to-end **medical imaging pipeline**
* Advanced **image preprocessing & augmentation**
* Comparison of **classification vs ordinal regression**
* Optimization using **Quadratic Weighted Kappa (QWK)**
* Handling of **class imbalance and noisy datasets**
* Designed for **real-world clinical deployment scenarios**

---

## Dataset

The model is trained on publicly available datasets:

* **EyePACS 2015**
* **APTOS 2019**

**Dataset characteristics:**

* ~91,000 retinal fundus images
* Labels: DR severity grades (0–4)
* Highly imbalanced distribution

**Data split:**

* 70% Training
* 15% Validation
* 15% Test

---

## Methodology

### Pipeline Overview

1. Image quality filtering (resolution, illumination, integrity)
2. Preprocessing & ROI extraction
3. Data augmentation
4. Feature extraction via CNN backbone
5. Model training & validation
6. Post-processing & evaluation

---

### Preprocessing Techniques

* Circular cropping (retinal region isolation)
* Green channel extraction
* Ben Graham normalization (contrast enhancement)
* Image resizing (224×224 / 512×512)
* Data augmentation:

  * Flips, rotations, zoom
  * Brightness/contrast adjustments

---

## Models

### 1. ResNet-50 (Baseline)

* Architecture: 50-layer residual network
* Input: 224×224 images
* Output: 5-class softmax classification
* Loss: Categorical Cross-Entropy

**Performance:**

* Accuracy: ~79%
* QWK: 0.62 – 0.68

---

### 2. DenseNet-121 (Proposed)

* Architecture: Dense convolutional network
* Input: 512×512 images
* Output: Continuous severity score (ordinal regression)
* Loss: Mean Squared Error (MSE)

**Key advantages:**

* Models **ordinal nature** of disease progression
* Reduces large misclassification errors
* More parameter-efficient (~66% fewer parameters)

**Performance:**

* QWK: ~0.78 – 0.79
* Improved recall for referable DR

---

## Evaluation Metrics

* **Primary Metric:** Quadratic Weighted Kappa (QWK)
* Accuracy
* Precision / Recall / F1-score
* Confusion Matrix
* Focus on **referable DR detection (grades 2–4)**

---

## Results Summary

| Model        | QWK       | Parameters | Approach           |
| ------------ | --------- | ---------- | ------------------ |
| ResNet-50    | 0.62–0.68 | ~23.6M     | Classification     |
| DenseNet-121 | 0.78–0.79 | ~7.9M      | Ordinal Regression |

**Conclusion:**
DenseNet-121 significantly outperforms the baseline by:

* Achieving higher QWK
* Reducing critical grading errors
* Using fewer parameters → better for deployment

---

## Technologies Used

* Python
* TensorFlow / Keras
* PySpark (data processing)
* OpenCV (image preprocessing)
* NumPy / Pandas

---

## Project Structure

```
├── data/                # Dataset (not included)
├── notebooks/           # Training & experiments
├── models/              # Saved models
├── preprocessing/       # Image preprocessing pipeline
├── utils/               # Helper functions
├── results/             # Evaluation outputs
└── README.md
```

---

## Applications

* Automated **medical screening systems**
* Clinical decision support tools
* Deployment in **resource-constrained environments**
* Early detection of vision-threatening diseases

---

## Limitations

* Class imbalance in datasets
* Performance sensitive to image quality
* Requires further validation in real-world clinical settings

---

## Future Work

* Advanced imbalance handling (e.g., focal loss)
* Model calibration & uncertainty estimation
* Real-world clinical validation
* Fairness and bias analysis across populations

---

## Authors

* Ali Al-Kelabi
* Ibrahim Adham Bin Mohd Aziz
* Althaf Rasheed Abubakkar
* Ritika Alla

---

## License

This project is intended for academic and research purposes.

---
