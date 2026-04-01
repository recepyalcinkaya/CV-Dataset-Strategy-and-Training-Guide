# Resources and Tools

## 🛠 Data Annotation Tools
* **CVAT (Computer Vision Annotation Tool):** Industry standard for video and image annotation.
* **LabelImg:** A simple, offline, fast tool for XML/TXT formats.
* **Roboflow:** A comprehensive platform for dataset management, versioning, and automated augmentation.

## 📚 Key Concepts and Readings
* **Data Augmentation:**
    * *Mosaic Augmentation:* Combines 4 different images to improve the detection of small objects (popularized by YOLOv4+).
    * *MixUp:* Overlays two images transparently, encouraging the model to make probabilistic predictions rather than overly confident ones.
* **Curriculum Learning:**
    * A strategy of training the model initially on "easy/clean" data only, and gradually introducing "hard/problematic" data into the training pipeline as the epochs progress.
* **IoU (Intersection over Union):**
    * A metric indicating how much the predicted bounding box overlaps with the ground truth bounding box.
