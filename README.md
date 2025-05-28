# Plant Disease Detection with Deep Learning
**YOLOv5 + Anvil Web App Integration**

---

## Project Overview

Plant diseases are responsible for up to **40% of global food production losses** (FAO). Early and accurate detection is crucial, but manual inspection is not scalable for large fields.  
This project leverages **deep learning** and **computer vision** to automate plant disease detection, providing a free, open-source solution accessible via a web app.

**Key Features:**
- **YOLOv5 model** for detecting and classifying strawberry plant diseases.
- **Web deployment with Anvil:** Upload plant images and get instant predictions.
- **Open-source and reproducible:** All code, data, and instructions included.

---

## Benefits of Automated Plant Disease Detection

- **Early Intervention:** Detect diseases before they spread.
- **Scalability:** Analyze large fields efficiently.
- **Data-Driven Farming:** Enable targeted irrigation or pesticide application.
- **Accessibility:** Free, open-source tool for researchers and farmers.

---

## Experimental Setup

### Data and Input Format

- **Source:** RoboFlow dataset (5,494 images, 12 original classes)
- **Filtered:** 5 strawberry disease/pest classes, split into:
    - **Training:** 810 images
    - **Validation:** 633 images
    - **Test:** 460 images
- **Classes:**  
    1. powdery_mildew  
    2. leaf_spot  
    3. gray_mold  
    4. blossom_blight  
    5. angular_leafspot  
- **Format:** JPG (416x416 px), YOLO TXT labels, YAML metadata

### Objective

- **Classify** strawberry plant images into disease categories with high accuracy.
- **Deploy** the model for real-time, web-based predictions.

---

## Notebook Structure

### Preprocessing

- Load images and labels from Google Drive.
- Adjust YAML configuration for data paths and classes.
- Filter and split the dataset into training, validation, and test sets.

### Model Training

- Use **YOLOv5** (Ultralytics, PyTorch-based) for object detection/classification.
- Initial training with default hyperparameters, then increase epochs for better accuracy.
- Evaluate using metrics: **Precision, Recall, mAP50**.

### Evaluation

- Track model performance on validation data after each training phase.
- Analyze improvements in precision, recall, and mAP50 as epochs increase.

### Deployment

- Export the trained model as a `.pt` file.
- Integrate with a Google Colab notebook for inference.
- Connect the notebook to an Anvil web app via Anvil Uplink for API-based predictions.

---

## Code & Web App Integration

The provided Colab notebook:
- **Installs dependencies** (YOLOv5, Anvil Uplink, OpenCV, PyTorch, etc.).
- **Loads the trained model and class names.**
- **Defines an Anvil server function** (`process_image`) to accept image uploads, run inference, and return predictions (including annotated images).
- **Waits for incoming requests** from the Anvil web app.

**Key Features:**
- Base64 image handling for web compatibility.
- Majority voting if multiple objects are detected.
- Error handling for invalid or empty images.

---

## Iterations & Results

### Baseline

- Initial training (1 epoch):  
  - **Precision:** 35.2%  
  - **Recall:** 20.0%  
  - **mAP50:** 13.2%
- Revealed need for more training and data cleaning.

### Improved Training

- 10 epochs:  
  - **Precision:** 79.4%  
  - **Recall:** 82.5%  
  - **mAP50:** 57.8%
- 300 epochs:  
  - **Precision:** 90.0%  
  - **Recall:** 80.5%  
  - **mAP50:** 87.6%
- **Significant improvement** with more epochs and stable hyperparameters.

### Deployment

- Model successfully deployed via Colab and Anvil.
- Real-time predictions with annotated image output.

---

## Lessons Learned

- **Data Quality Matters:** Cleaning and proper labeling are critical.
- **Model Tuning:** Increasing epochs and careful hyperparameter selection boost performance.
- **Open-Source Tools:** Google Colab, PyTorch, and Anvil enable rapid prototyping and deployment.
- **Web Integration:** API-based deployment makes the model accessible and user-friendly.

---

## Future Work & Outlook

- **Expand** to more plant species and diseases.
- **Incorporate** advanced data augmentation and transfer learning.
- **Apply** explainable AI techniques for better model transparency.
- **Develop** a mobile app or interactive dashboard for field use.
- **Integrate** additional data sources (e.g., weather, soil) for holistic crop health monitoring.

---

## How to Use

1. **Clone this repository** and open the Colab notebook.
2. **Mount your Google Drive** and ensure the dataset and trained model are accessible.
3. **Install dependencies** as specified in the notebook.
4. **Set your Anvil Uplink key** to connect the notebook with your Anvil web app.
5. **Run the notebook** to start the inference server.
6. **Use the Anvil web app** to upload plant images and receive instant disease predictions with annotated images.

---

## References

- [Ultralytics YOLOv5](https://github.com/ultralytics/yolov5)
- [Anvil Web Apps](https://anvil.works/)
- [RoboFlow Datasets](https://roboflow.com/)
- [FAO Plant Health Statistics](https://www.fao.org/)

---

**This project demonstrates the power of deep learning and open-source tools for tackling real-world agricultural challenges, making advanced technology accessible to everyone.**
