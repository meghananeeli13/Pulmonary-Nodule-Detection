# Pulmonary Nodule Detection Using YOLOv7 and 3D CNN

---

## 1. Project Overview

Lung cancer is one of the leading causes of cancer-related deaths worldwide. Early detection of pulmonary nodules (small growths in the lung) in CT scans can significantly improve patient outcomes. This project aims to automate the detection of these nodules using advanced deep learning techniques.

We use the **LUNA16 dataset**, which contains 3D CT scans of lungs, and apply a combination of 3D Convolutional Neural Network (CNN) preprocessing and the **YOLOv7 object detection model** to identify pulmonary nodules.

---

## 2. Dataset Description

- **Dataset:** LUNA16  
- **Type:** 3D lung CT scans stored as `.mhd` (MetaImage) files  
- **Challenge:** The CT scans are 3-dimensional, but YOLOv7 works on 2D images, so the scans need to be sliced into 2D images before training.  
- **Annotations:** The dataset contains ground truth nodule locations that are used to generate bounding box labels for training.

---

## 3. Project Workflow

### Step 1: Preprocessing  
- Read 3D CT scan files using SimpleITK (or similar libraries).  
- Convert the 3D volume into 2D PNG slices — each slice corresponds to a cross-sectional image of the lungs.  
- Save these slices in structured folders for easy access.

### Step 2: Annotation Generation  
- Use nodule coordinates to generate bounding box labels in **YOLO format** for each 2D slice.  
- YOLO format requires normalized bounding box coordinates: `(class_id, x_center, y_center, width, height)` relative to image size.  
- Save labels as `.txt` files corresponding to each image.

### Step 3: Dataset Organization  
- Organize images and labels into `train` and `val` folders.  
- Prepare a `data.yaml` file for YOLOv7 that specifies dataset paths, number of classes, and class names.

### Step 4: Training Setup  
- Use YOLOv7 pretrained weights for transfer learning.  
- Configure hyperparameters such as batch size, number of epochs, and image size.  
- Prepare the training script command.

### Step 5: Model Training  
- **Training is set up but pending execution** due to hardware limitations.  
- Once run, the model will learn to detect nodules in 2D slices.  
- After training, model evaluation will be performed using metrics like mAP (mean Average Precision), precision, and recall.
