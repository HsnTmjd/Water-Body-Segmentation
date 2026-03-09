# Multimodal Water Body Segmentation (RGB + Thermal)

This project implements a **multimodal semantic segmentation model** for detecting water bodies using **RGB and Thermal Infrared (TIR) data**.  
By combining optical and thermal information, the model reduces false detections caused by shadows or dark vegetation.

## Key Features

- **4-Channel Input (RGB + Thermal)**  
  Custom data loader stacks RGB images with a thermal channel to create a 4-channel input tensor.

- **U-Net with ResNet50 Backbone**  
  Uses a ResNet50 encoder for strong feature extraction and accurate segmentation.

- **Advanced Preprocessing**
  - **Unsharp Masking** on RGB channels to enhance shoreline edges  
  - **Median Filtering** on thermal data to reduce sensor noise

- **Shadow Reduction**  
  The model distinguishes water from shadows by checking both optical and thermal signals.

## Methodology

Water and shadows can look similar in RGB imagery.  
Thermal data helps differentiate them:

- **Water:** Optically dark + Thermally cold  
- **Shadow/Land:** Optically dark + Thermally warm

## Training

- **Loss Function:** Dice Loss  
- **Task:** Binary semantic segmentation (Water / Non-water)

## Performance

The **RGB-Thermal fusion model** achieves improved **IoU scores** and reduces false positives, especially in **complex regions such as reservoirs and delta landscapes**.
