# Road Damage Detection – Crackathon (IIT Bombay)

## Overview
This repository contains the source code and commands used to train and evaluate an object detection model for the IIT Bombay Crackathon. The task is to detect and classify road damage using bounding boxes.

## Dataset
- Road Damage Detection 2022 (RDD2022)
- Official randomized dataset provided by the organizers
- No external data used

## Model
- YOLOv8 Object Detection
- Pretrained weights (allowed by rules)

## Classes
0 – Longitudinal Crack  
1 – Transverse Crack  
2 – Alligator Crack  
3 – Other Corruption  
4 – Pothole  

## Training
```bash
yolo detect train model=yolov8m.pt data=data.yaml epochs=45 imgsz=640 batch=12 optimizer=AdamW

Inference (Test Set)

yolo detect predict \
model="runs/phase1_best/weights/best.pt" \
source="dataset/test/images" \
save_txt=True \
save_conf=True

Each test image generates a .txt file with:

<class_id> <x_center> <y_center> <width> <height> <confidence_score>

All prediction files were placed in a predictions folder and zipped as submission.zip.

Reproducibility

Commands provided are sufficient to reproduce training and inference

No test labels accessed

All competition rules followed
