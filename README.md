#  Kidney Stone Detection using a YOLOv10 & SegFormer Framework 🔬


This repository contains the official code and report for the "Kidney Stone Detection" project for the University of Tehran's Image Processing course. The project introduces a novel two-stage, expert-based framework named **Localizer-Analyst** to accurately detect kidney stones in medical images.

---

### 📋 Table of Contents
1. [Overview](#-overview)
2. [Key Features](#-key-features)
3. [Architecture: The Localizer-Analyst Framework](#-architecture-the-localizer-analyst-framework)
4. [Performance Results](#-performance-results)
5. [Setup and Installation](#-setup-and-installation)
6. [Usage](#-usage)


---

### 📖 Overview

Kidney stone detection is a critical diagnostic task that can be challenging due to the variability in stone size, shape, and visibility. This project tackles this challenge by developing a robust, two-stage deep learning pipeline that synergizes the strengths of object detection and semantic segmentation. The system first uses a high-recall detector (the Localizer) to identify all potential stone candidates and then employs a high-precision segmentation model (the Analyst) to verify each proposal. This coarse-to-fine approach significantly improves upon baseline performance, particularly by increasing recall while simultaneously boosting precision.

---

### 🌟 Key Features

- **Two-Stage Expert Framework:** A novel Localizer-Analyst architecture that reduces false positives without compromising sensitivity.
- **State-of-the-Art Models:** Implements **YOLOv10l** for rapid and sensitive object localization and **SegFormer (MiT-B3)** for precise, pixel-level analysis.
- **Superior Performance:** Outperforms the baseline mAP@0.5 by over **7.4%**, with a significant **8.3%** relative improvement in recall.
- **Complete Pipeline:** The included Jupyter Notebook provides the full code for data preparation, model training, and evaluation.
- **Reproducible Research:** The repository is structured to allow for easy replication of the experimental results.

---

### 🏗️ Architecture: The Localizer-Analyst Framework

The proposed architecture decomposes the detection task into two sequential stages, handled by specialized "expert" models.

1.  **The Localizer (YOLOv10l):** Performs a rapid scan of the input image to generate a set of candidate Regions of Interest (RoIs) with high recall.
2.  **The Analyst (SegFormer):** Performs a detailed, pixel-level examination of each RoI, producing a segmentation heatmap to confirm the presence of a stone.
3.  **The Fusion Manager:** Integrates the outputs from both stages, calculating a refined confidence score that effectively validates or rejects the initial proposals.

---

### 📊 Performance Results

The fused model demonstrates a significant improvement over the provided baseline, validating the effectiveness of the two-stage approach.

#### Final Fused Model Performance
| Dataset Split | Precision | Recall | mAP@0.5 |
| :------------ | :-------- | :----- | :------ |
| Validation    | 0.8530    | 0.8215 | 0.8359  |
| **Test**      | **0.8619**| **0.8080** | **0.8275** |

#### Comparison with Baseline (on Test Set)
| Metric    | Baseline Performance | Fused Model | Relative Improvement |
| :-------- | :------------------- | :---------- | :------------------- |
| Precision | 0.8548               | **0.8619**  | +0.83%               |
| Recall    | 0.7461               | **0.8080**  | **+8.30%**           |
| mAP@0.5   | 0.7700               | **0.8275**  | **+7.47%**           |

---

### ⚙️ Setup and Installation

Follow these steps to set up the project environment.

**Prerequisites:**
- Python 3.8+
- Jupyter Notebook

- Download the [Kidney Stone Images dataset from Kaggle](https://www.kaggle.com/datasets/safurahajiheidari/kidney-stone-images).
- Unzip the dataset and place it in the project directory. The notebook assumes the dataset is located at `/content/drive/MyDrive/kidney-dataset`, so you may need to adjust the paths in `SegFormer_Kidney_Stone_Detection.ipynb` to match your local directory structure (e.g., `kidney-dataset/`).

---

### 🚀 Usage

The primary code is contained within the `SegFormer_Kidney_Stone_Detection.ipynb` Jupyter Notebook.

- **Running in Google Colab (Recommended):**
  1. Upload the `SegFormer_Kidney_Stone_Detection.ipynb` notebook and the `kidney-dataset` folder to your Google Drive.
  2. Update the `PROJECT_ROOT` and `DATASET_PATH` variables in the first cell to point to the correct locations in your Drive.
  3. Run the cells sequentially to execute the data preparation, model training, and evaluation pipeline.

- **Running Locally:**
  1. Ensure all dependencies are installed and the dataset is in the correct location.
  2. Launch Jupyter Notebook: `jupyter notebook`
  3. Open `Success.ipynb` and execute the cells.
