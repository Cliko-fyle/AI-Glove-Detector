# 🧤AI Glove Detector using YOLOv8

This project detects **gloved hands** vs **bare hands** in images using a trained YOLOv8 model. The pipeline includes dataset loading, model training, inference with annotated outputs, and generating JSON logs for detections.


## Dataset
- **Name:** Glove
- **Source:** https://universe.roboflow.com/glove-uylxg/glove-q7czq
- **Classes:**
  - `glove` (hand with glove)  
  - `no_glove` (bare hand)
- **Contents:**
  - train
    - images
    - labels
  - valid
    - images
    - labels
  - test
    - images
    - labels
  - data.yaml

## Model Used
YOLOv8m (medium) and YOLOv8l (large)

## Preprocessing / Training
- Images resized to **640x640**
- Data augmentation:
  - Rotate
  - Translate
  - Scale
  - Shear
  - Flip
- Trained with **YOLOv8m** for 30 epochs and saved the best weights
- Validation done on **valid** set, tested on **test** set

## What Worked
- YOLOv8m provided high accuracy with fast training when used Google Colab T4 GPU
- The mAP@50 reached **0.995** on the test dataset

## What Didn’t Work
- Some misclassifications occurred when bare hands and other covered objects(shoes) were partially visible in the same image
- The mAP50-95 was comparatively lower due to variations in glove color, lighting, and hand positions


