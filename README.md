## Image Segmentation Model for ISIC 2016 Dataset

## Overview
This project is an **image segmentation model** designed to **segment melanoma regions** from dermoscopic images in the ISIC 2016 dataset. The model uses deep learning techniques, specifically **U-Net** and **U-Net with ResNet Encoder**, to identify and segment melanoma from skin images.

 **Current Status:** Segmenting melanoma regions from skin lesions images  
 **Models Used:** **U-Net** and **U-Net with ResNet-34 Encoder**

---

## Dataset
- **Source**: [ISIC 2016 Dataset](https://challenge.isic-archive.com/)
- **Number of Samples**: 
  - **Train**: 810 images  
  - **Validation**: 90 images  
  - **Test**: 379 images
- **Number of Classes**: 2 (Background and Melanoma)
  - `0` → Non-melanoma region
  - `1` → Melanoma (Tumor region)
- **Number of Channels**: 3 (RGB images)
- **Target Variable**: Binary segmentation mask indicating the melanoma region
- **Data Type**: The dataset consists of **dermoscopic images** of skin lesions with corresponding **segmentation masks** that outline the melanoma area. The images are RGB (3 channels), and the masks are single-channel binary images.
---

## Model Development

### **Data Preprocessing**
- **Data Augmentation**: Applied various augmentations to images, including:
  - Random rotations (30 degrees)
  - Random horizontal and vertical flips
  - Random color jitter (brightness, contrast, and saturation) for image variability
- **Normalization**: Standardized image pixel values to ensure model consistency
- **Segmentation Masks**: Masks were used in binary format (0 for background, 1 for melanoma).

### **Model Training & Selection**
- **U-Net**: A deep learning model for semantic segmentation, used for pixel-wise classification of melanoma regions.
- **U-Net with ResNet Encoder**: This version of U-Net uses a **pre-trained ResNet-34 encoder** for improved feature extraction.
- Both models were trained using **binary cross-entropy loss** and **Dice coefficient** to measure segmentation performance.


### **Model Evaluation**
- **Accuracy**: Evaluated using the Dice coefficient to measure the overlap between predicted and ground truth masks.
  **U-Net Model**: Achieved an average Dice coefficient of 75% on the test dataset.
  **U-Net with ResNet Encoder**: Achieved an improved Dice coefficient of 85% on the test dataset.
-   U-Net with ResNet Encoder was chosen as the final model due to better performance during training and validation.
  
---

## Installation & Usage
### **Prerequisites**
Ensure **Python 3.8+** is installed along with:
```bash
pip install medsegbench tqdm torch torchvision
```
---
### **Running the Notebook**
 Open the Colab notebook:  
[Image Segmentation ISIC 2016 Colab Notebook](https://colab.research.google.com/drive/1W4NKWL1D2m-UOln_o4NiSK2Z2YueHHGG)

 Run all cells in the notebook to preprocess data, train the models, and evaluate results.

---

## Acknowledgments
- **ISIC Archive** for providing the dataset
- **Scikit-learn** for offering ML tools
