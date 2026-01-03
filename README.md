# Road Damage Detection – Crackathon (IIT Bombay)

## Overview
This repository contains the complete source code and commands used to train and evaluate an object detection model for the IIT Bombay Crackathon.

The objective is to automatically detect and classify different types of road damage from images using bounding boxes.

## Dataset
- Road Damage Detection 2022 (RDD2022)
- Official randomized dataset provided by the competition organizers
- Only the provided dataset was used (no external data)

## Model Architecture
- YOLOv8 Object Detection Model
- Pretrained YOLOv8 weights were used, as permitted by the competition rules
- The model outputs bounding boxes in YOLO TXT format

## Damage Classes
0 – Longitudinal Crack  
1 – Transverse Crack  
2 – Alligator Crack  
3 – Other Corruption  
4 – Pothole  

## Training Strategy
- Image size: 640 × 640
- Optimizer: AdamW
- Batch size: 12
- Epochs: 45
- Data augmentation: Mosaic, horizontal flip, scaling
- Best model checkpoint selected based on validation mAP

## Training Command
The following command was used to train the detection model:

```bash
yolo detect train model=yolov8m.pt data=data.yaml epochs=45 imgsz=640 batch=12 optimizer=AdamW

Inference (Test Set Predictions)

The following command was used to generate predictions on the test set in the required YOLO TXT format:

yolo detect predict \
model="runs/phase1_best/weights/best.pt" \
source="dataset/test/images" \
save_txt=True \
save_conf=True

This command generates one .txt file per test image.
Each file contains predictions in the format:

<class_id> <x_center> <y_center> <width> <height> <confidence_score>

All prediction files were placed inside a folder named predictions and compressed into submission.zip for final submission.

Evaluation

Evaluation metric: Mean Average Precision (mAP)

Best validation performance achieved: mAP@0.5 ≈ 0.58–0.59

The model follows a rule-compliant object detection pipeline


Reproducibility

The code is fully reproducible using the provided commands

No test labels were accessed during training or inference

All competition rules and constraints were strictly followed
