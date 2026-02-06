# Tomato Leaf Disease Classification (Transfer Learning + Grad-CAM)

This repository contains the **training** and **inference** code for the research:

**"Comparative Study of Lightweight and Deep CNN Architectures for Tomato Leaf Disease Classification Using Transfer Learning and Grad-CAM Visualization"**
---

## Overview
This project evaluates multiple Convolutional Neural Network (CNN) architectures for automated tomato leaf disease classification using a transfer learning approach and Grad-CAM for model interpretability.

**Architectures evaluated:**
- ResNet50 (deep CNN)  
- MobileNetV2 (lightweight CNN)  
- EfficientNetB0 (balanced architecture)  

The study analyzes the trade-offs between **classification performance, computational efficiency, and interpretability**. 

The dataset used is the **PlantVillage tomato leaf subset**, consisting of **18,160 RGB images across 10 classes** (nine diseases + one healthy class). 

---

## Repository Structure

```
├── Tugas2_Visi_Komputer_Kelompok_10.ipynb            # Training notebook
├── Tugas2_Visi_Komputer_inferensi_Kelompok_10.ipynb  # Inference notebook
└── README.md
```

---

## Training Scenario

All models were trained under identical settings to ensure a fair comparison.

**Data Split**
- Training: 80%  
- Validation: 10%  
- Testing: 10% 

**Preprocessing**
- Image resizing to **224 × 224**
- Architecture-specific preprocessing aligned with ImageNet
- Data augmentation: horizontal flip, small rotations, and slight zoom  

**Training Configuration**
- Optimizer: Adam  
- Batch size: 32  
- Epochs: 30  
- Loss function: Categorical Cross-Entropy  
- Early stopping to reduce overfitting 

**Transfer Learning Schemes**
1. Freeze-all layers (train classifier only)  
2. Fine-tuning with **20%** unfrozen layers  
3. Fine-tuning with **40%** unfrozen layers  

Grad-CAM was applied to the best-performing model to verify that predictions focus on disease-relevant regions.  

---

## Results

- **EfficientNetB0 with 40% fine-tuning** achieved the highest classification performance across evaluation metrics. 
- **MobileNetV2** delivered the fastest inference time, making it suitable for mobile or edge deployment.  
- **ResNet50** provided stable performance but required higher computational cost. 

Grad-CAM visualizations showed that the model consistently focuses on biologically meaningful regions such as lesions, discoloration patterns, and infected areas. 

---

## Conclusion

This study demonstrates that model selection should depend on deployment needs:

- **EfficientNetB0** is preferred when accuracy and interpretability are the primary goals.  
- **MobileNetV2** is more suitable for real-time applications requiring low latency.  

Although EfficientNetB0 is parameter-efficient, it exhibited longer inference times, highlighting that parameter efficiency does not always translate to runtime efficiency. 

Future work may explore model optimization techniques, transformer-based architectures, and evaluation on real-world datasets with more complex backgrounds.  

