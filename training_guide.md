# Training and Hyperparameter Guide

This section covers the key technical points to consider when training a model on the dataset.

## 1. How to Determine the Number of Epochs?
Setting a fixed number (e.g., "100 epochs") is not always the correct approach. The following strategy should be adopted:

* **Starting Point:** Generally, you can start with 100-300 epochs (this varies depending on the dataset size).

* **Early Stopping:** If the "Validation Loss" stops decreasing and starts increasing for a certain period (e.g., over a patience of 10-20 epochs), training should be automatically halted. This is a clear indicator that "Overfitting" has begun.

* **Rule of Thumb:** If Training Loss is decreasing but Validation Loss is increasing -> **Overfitting**. You should decrease the number of epochs or increase Regularization techniques (Dropout, Weight Decay).

## 2. Batch Size
* Select the highest power of 2 (16, 32, 64) that your GPU memory permits.
* Small Batch Size (8-16): Creates noisier gradients, which sometimes helps the model escape local minima (acts as a regularization effect).
* Large Batch Size (64+): Provides more stable training, but the "Learning Rate" needs to be increased proportionally.

## 3. Key Metrics to Monitor
Relying solely on overall "Accuracy" is insufficient. Track the following metrics for object detection tasks:
* **mAP@0.5 (mean Average Precision):** Indicates how accurately the object is classified and how precisely the bounding box is drawn.
* **Recall:** How many of the existing objects did we miss? (This is absolutely crucial in safety-critical ADAS systems).
* **Precision:** Out of the objects we detected, how many are actually correct predictions?
