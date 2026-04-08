# 🩸 Forensic Gunshot Wound Classification: A Vision Transformer (ViT) Benchmark

## 🩺 1. Problem Definition & Objectives
While CNNs have shown great success in forensic imaging, **Vision Transformers (ViT)** offer a unique advantage by capturing global spatial dependencies and patch-based morphological markers. This project benchmarks state-of-the-art Transformer architectures—**ViT-Small** and **Swin-Transformer**—to evaluate their efficacy in distinguishing **Entrance** vs. **Exit** gunshot wounds.

By utilizing **Attention Mechanisms**, this study investigates whether Transformer-based models can more accurately identify subtle forensic indicators, such as the continuity of abrasion rings and the complexity of radial lacerations, compared to traditional convolutional approaches.

## 📊 2. Dataset Specifications
The models were trained and evaluated using the **FDCPUnBGunshotDB**, following the same rigorous preprocessing pipeline as the previous CNN benchmark.

* **Dataset Source:** [FDCPUnBGunshotDB GitHub](https://github.com/pedrogarciafreitas/FDCPUnBGunshotDB)
* **Classes & Distribution:**
  - **Entrance Wounds:** 1,883 images (Class 0)
  - **Exit Wounds:** 671 images (Class 1)
* **Transformer-Optimized Preprocessing:**
  - **Center-Focus Strategy:** Implemented a **CenterCrop (224x224)** approach to focus strictly on the wound's central morphology and align with ViT patch requirements.
  - **Imbalance Handling:** Utilized **Weighted Cross-Entropy Loss** (Ratio 1:2.8) to ensure high sensitivity for the minority class (Exit wounds).

## 🚀 3. Key Technical Features
* **Transformer Benchmarking:** Comprehensive evaluation of **ViT-Small (patch16)** and **Swin-Tiny (window7)** using the `timm` (PyTorch Image Models) library.
* **Hierarchical Feature Extraction:** Implementation of Swin Transformer to capture multi-scale forensic textures through shifted window mechanisms.
* **Explainable AI for Transformers:** Specialized **Grad-CAM** implementation with `reshape_transform` to visualize attention maps over 1D tokens, ensuring clinical relevance.
* **Hardware:** Optimized for training on **Google Colab L4 GPU** environments, achieving high-precision results within minimal training time.

## 📈 4. Performance Metrics (Benchmark Results)
Both Transformer models demonstrated superior performance, reaching an accuracy of **91.1%** and showing exceptional reliability in identifying Entrance wounds.

| Model | Accuracy | Entrance F1-Score | Exit F1-Score | Note |
| :--- | :---: | :---: | :---: | :--- |
| **ViT-Small** | **91.1%** | **0.94** | **0.82** | **Superior Entrance Recall (96%)** |
| **Swin-Tiny** | **91.1%** | **0.94** | **0.82** | **Robust Contextual Awareness** |
| ResNet50 (Baseline)| 87.0% | 0.91 | 0.75 | Previous CNN Benchmark |

---

## 🔍 Visual Analysis Comparison

### A. Confusion Matrix (CM) Results
The Transformers show significantly improved recall for Entrance wounds (96.1%), effectively minimizing false negatives in forensic documentation.

#### 1. ViT-Small Confusion Matrix
![ViT-Small CM](results/CM_vit_small_patch16_224.png)

#### 2. Swin-Tiny Confusion Matrix
![Swin-Tiny CM](results/CM_swin_tiny_patch4_window7_224.png)

---

### B. Model Interpretability (Grad-CAM)
We verified the models' focus using specialized Grad-CAM for Transformers. The attention is concentrated on the **wound margins** and **abrasion collars**, mimicking the diagnostic logic of forensic pathologists.

#### 1. ViT-Small Focus Analysis
![ViT GradCAM](results/vit_small_Grad_CAM.png)

#### 2. Swin-Tiny Focus Analysis
![Swin GradCAM](results/swin_tiny_Grad_CAM.png)

---

## 📝 Research Collaboration
This project is part of an ongoing research collaboration with **Dr. Lorenzo Gitto**, a Forensic Pathologist at the Cook County Medical Examiner's Office. This benchmarking provides empirical evidence for the use of Transformer-based architectures as objective decision-support tools in forensic science.

---

## 🧑‍⚕️ About the Author
**Hee Jae Ryu (HEE JAE RYU), MD**
* **Pathology Residency Applicant (2026 Match)**
* **MD, Chungbuk National University College of Medicine**
* **Content Creator at 'CowEye' (1.68M+ Subscribers)**
* **Primary Interests:** Digital Pathology, Forensic Science, and AI-driven Diagnostics
