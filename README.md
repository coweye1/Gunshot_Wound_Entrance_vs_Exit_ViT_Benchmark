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
| **ViT-Small** | **91.1%** | **0.94** | **0.82** | **Superior Entrance Recall (9
