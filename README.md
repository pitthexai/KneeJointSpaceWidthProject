# Automated Measurement of Knee Joint Space Width (JSW) from Radiographs Using Deep Learning

## Overview
Knee osteoarthritis (KOA) is a degenerative joint condition that is often characterized by the narrowing of the knee joint space width (JSW). Traditional methods for measuring JSW are manual, time-intensive and are subject to variability. Thus, developing accurate and consistent methods for JSW measurement is essential for both diagnosing and monitoring the progression of KOA. 

This project aims to develop a deep learning-based pipeline for the automated measurement of JSW from knee radiographs. The proposed pipeline integrates computer vision techniques for knee joint localization, joint space segmentation, and JSW measurement. By utlizing state-of-the-art models such as YOLOv11 and U-Net, the project seeks to achieve high accuracy and robustness in JSW prediction, thereby advancing clinical assessment tools for KOA.

## Objectives
The primary objectives for this project is to design and evaluate a comprehensive deep learning pipeline for automated JSW measurement. The specific objectives include:

1. Localization of the Knee Joint Area:
   - Train and validate a YOLOv11 model to detect and localize the left and right knee joints in complete radiographs.
   - Evaluate the localization accuracy using bounding box prediction on unseen test data
  
2. Segmentation of the Knee Joint Space
   - Develop a segmentation model based on U-net to segment the knee joint space
   - Utilize the YOLOv11-based cropped radiographs/segmentation masks for training 
   - Assess overall segmentatation performance using Intersection over Union (IoU) and Dice score
  
3. Measurement of JSW:
   - Train a predictive model to measure JSW for the medial and lateral compartments
   - Use both radiographs and segmentation masks and features to the measurement model
  
4. Testing on Unseen Data
   - Test the developed pipeline end-to-end on unseen radiographs to predict the medial and lateral JSW values
   - Evaluate the robustness and generalizability of the pipeline
  

## Dataset
The dataset for this project consists of annotated knee radiographs and associated metadata, structured as follows:

Training Dataset:
- Images: 643 knee radiographs for training, validation, and testing across the pipeline tasks.
- Localization Annotations: Bounding box annotations for knee joint localization in PASCAL-VOC format.
- Segmentation Annotations: Binary masks of knee bony anatomy for a subset of images.
- Measurements.csv: Ground truth JSW measurements (medial and lateral compartments) for both left and right knees.


Test Dataset:
- Images: Unannotated knee radiographs for evaluating the final pipeline.
- Labels: Ground truth JSW measurements are withheld to assess model performance.

Data Usage:
- Localization tasks will use bounding box annotations to train YOLOv11.
- Segmentation tasks will utilize the cropped radiographs and corresponding segmentation masks to train U-Net.
- JSW measurement tasks will leverage the radiographs, segmentation outputs, and measurements.csv for training and validation.


## Evaluation Metrics:
The pipeline models will be evaluated using the following metricsL
- Localization: mean Average Precision (mAP).
- Segmentation: IoU and Dice coefficient.
- JSW measurement: Mean Absolute Error (MAE) and R^2

