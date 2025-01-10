# # Pitt HexAI Computer Vision Challenge: Automatic Joint Space Width Measurement

## Challenge Overview
The objective of this challenge is to develop a deep learning-based pipeline for the automated measurement of knee joint space width (JSW) from knee X-rays. Accurate JSW measurement is critical for diagnosing and monitoring knee osteoarthritis (KOA). Your solution should utilize computer vision techniques to ensure consistency and reproducibility through the following key steps:

1.	Localization of the Knee Joint Area
2.	Segmentation of the Knee Joint Space
3.	Measurement of Joint Space Width

***Important Note: This challenge must be completed individually. Collaboration or seeking assistance from others is not allowed. Additionally, the use of generative AI tools (e.g., ChatGPT, Gemini, Ollama, or similar) is strictly prohibited. Submissions found to rely on such tools for code generation or methodology will be disqualified.***

## Dataset
The dataset, which can be downloaded [from Google Drive using this link](https://drive.google.com/file/d/1TtAJUFsw3jbhbSdfxvt0FCyTw9PFOmvr/view?usp=sharing), consists of the following components:
- Training.zip: This file contains the following directories and files
  - Images: Contains a set of 643 knee radiographs for training, validation, and testing of YoloV11, segmentation, and JSW models. 
  - Localization_Annotations: Contains bounding box annotations for the provided images for training, validating, and testing a YOLOv11 localization model
  - Segmentation_Annotations: Includes knee radiographs and corresponding knee bony anatomy segmentation masks for a subset of the provided images for training, validating, and testing a segmentation model.
  -	Measurements.csv: Provides ground truth measurements of the knee joint space for both the medial and lateral compartments for the left and right knees (SIDE = 1 is Left, Side=2 is Right)
  -	***Note: You should use this data for training, validation, and testing individual components of your pipeline. This will be needed for certain parts of your pipeline!***
- Test.zip: Contains unannotated and uncropped knee radiographs to evaluate your final pipeline on unseen data. The labels are not included with the test data. 

## Challenge Tasks
### Task 1: Localization of the Knee Joint Area
- Create a train, validation, and test set that can be utilized by YOLOv11. Note: You will need to convert provided annotations to YOLO format. 
- Train and validate a YOLOv11 model using the provided Localization dataset to detect the left and right knee joints. ***Hint: Look into using the Ultralytics library.***
- Submit bounding box predictions for your test images and include a few sample visualizations of the results.

### Task 2: Localizing the Segmentation Dataset
- Convert the knee bony anatomy segmentation masks to binary masks. ***Hint: Use SimpleITK to load the annotations***
- Apply your trained YOLO model to crop the knee joint regions from the radiographs and annotations in the Segmentation dataset.
- Output cropped images and their corresponding annotation masks.

### Task 3: Knee Joint Space Segmentation
- Train and validate s U-Net model using the cropped knee radiographs and annotation masks from Task 2 to segment the knee joint space. ***Hint: Look into using the PyTorch Segmentation Models library***
-	Provide segmentation predictions and evaluation metrics for your test set, including a few sample masks.

### Task 4: JSW Measurement 
- Train and validate a model to measure the JSW for the medial and lateral compartments using both the cropped knee images and segmentation masks. The provided dataset (measurements.csv) provides measurements across the medial and lateral joint. (Medial = Measures start with V00JSW and Lateral = Measures start with V00LJSW)
-	Report the JSW measurements for your test set.
-	For reference, you may consult the following paper: https://ieeexplore.ieee.org/abstract/document/10635236. 

### Task 5: Testing on Unseen Data
-	Apply your full pipeline to the radiographs in Test.zip and generate final JSW predictions for the medial and lateral compartments.
-	Submit the final JSW measurements in a CSV file.

## Submission Requirements
1.	Code: Provide all scripts, along with clear instructions on how to run them.
2.	Write-Up: Include a detailed explanation of the methods and results for each task.
3.	Final Output: Submit a CSV file containing JSW measurements for the unseen test set.

Please upload and share your code, results, and write-up in a shared OneDrive or Google Drive folder. Share the directory with: ngl18@pitt.edu. 

## Evaluation Criteria
Submissions will be evaluated based on:
-	Accuracy of localization, segmentation, and JSW measurement.
-	Robustness of the pipeline on unseen test data.
-	Clarity of the documentation and reproducibility of the code.

## Due Date
This challenge is due on Monday, December 30, 2024 by 11:59pm. 
