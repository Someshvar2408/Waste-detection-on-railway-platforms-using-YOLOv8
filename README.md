
# Waste Detection on Railway Platforms Using YOLOv8  

This repository contains the code, datasets, and resources for detecting waste on railway platforms in Chennai, India. The project leverages a video dataset converted into frames and processed using the YOLOv8 object detection framework for accurate and efficient waste detection.  

## Table of Contents  
- [Introduction](#introduction)  
- [Features](#features)  
- [Dataset](#dataset)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Training Process](#training-process)  
- [Validation](#validation)  
- [Prediction and Results](#prediction-and-results)  
- [Contributing](#contributing)  
- [License](#license)  

## Introduction  
Efficient waste management is a critical aspect of maintaining cleanliness, especially in public spaces like railway platforms. This project focuses on creating an AI-powered waste detection system using YOLOv8 to automate waste identification, enabling timely intervention by cleaning authorities.  

## Features  
- Waste detection using YOLOv8 pre-trained model  
- Custom dataset collected from railway platforms in Chennai  
- Optimization of detection accuracy through post-processing  
- Deployment-ready trained model for real-time waste detection  

## Dataset  
The dataset consists of video footage from railway platforms in Chennai, India, which has been converted into individual image frames. Images are annotated for training, validation, and testing purposes using [Roboflow](https://roboflow.com).  

## Installation  
Follow the steps below to set up the project environment:

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/waste-detection-yolov8.git
   cd waste-detection-yolov8
   ```

2. Install the required dependencies:
   ```bash
   pip install ultralytics roboflow
   ```

3. Verify GPU support:
   ```bash
   !nvidia-smi
   ```

## Usage  
### Dataset Preparation  
1. Import the dataset from Roboflow using the API key:
   ```python
   from roboflow import Roboflow
   rf = Roboflow(api_key="your_api_key")
   project = rf.workspace("waste-detection-f8nuy").project("waste-detection-wrre8")
   dataset = project.version(1).download("yolov8")
   ```

### Training the Model  
1. Train the YOLOv8 model:
   ```bash
   yolo task=detect mode=train model=yolov8m.pt data={dataset.location}/data.yaml epochs=50 imgsz=640
   ```

### Validation  
2. Validate the trained model:
   ```bash
   yolo task=detect mode=val model=/content/runs/detect/train2/weights/best.pt data={dataset.location}/data.yaml
   ```

### Prediction  
3. Use the model for predictions on the test dataset:
   ```bash
   yolo task=detect mode=predict model=/content/runs/detect/train2/weights/best.pt conf=0.5 source={dataset.location}/test/images save_txt=true
   ```

## Training Process  
- **Model:** YOLOv8m pre-trained model  
- **Epochs:** 50  
- **Image Size:** 640x640  
- **Training Command:**  
  ```bash
  yolo task=detect mode=train model=yolov8m.pt data={dataset.location}/data.yaml epochs=50 imgsz=640
  ```

## Validation  
- Results and confusion matrix are generated and stored in `/content/runs/detect/train2/`.  


