# Dataset Strategy and Distribution Ratios

This document outlines the data engineering strategy designed to ensure the model operates robustly under real-world conditions.

## 1. Data Composition
To ensure a deep learning model performs well in the field, not just in a laboratory environment, the following distribution is targeted within the dataset:

### A. Nominal (Clean) Data (60% - 70%)
* **Definition:** Well-lit, standard-angle images where the object is clearly visible.
* **Objective:** Allows the model to learn the fundamental features of the object (shape, color, texture). Baseline accuracy (mAP) is established with this data.

### B. Hard-Positive / Problematic Data (20% - 25%)
* **Definition:** Noisy data that the model will find difficult to detect.
    * **Occlusion:** 10% - 50% of the object being covered by another object.
    * **Blur:** Motion blur or loss of focus.
    * **Lighting:** Overly bright (glare) or very dark (shadow) environments.
    * **Deformation:** Crushed, bent, or faded states of the object.
* **Objective:** To prevent overfitting and ensure the model can generalize well under harsh and challenging conditions.

### C. Negative (Background) Data (10%)
* **Definition:** Images that **do not contain** the object to be detected at all.
* **Objective:** To reduce the False Positive rate. Prevents the model from mistaking every similar background shape for the target object.

## 2. Data Splitting
The dataset should be divided into 3 partitions with the following ratios:
* **Train (70%):** The primary data where the model updates its weights.
* **Validation (20%):** Used for hyperparameter tuning and Early Stopping checks during training. (Never included in the actual training loop).
* **Test (10%):** The model's performance on "unseen" data after training is complete. **Important:** The test set must include the most challenging real-world scenarios.
