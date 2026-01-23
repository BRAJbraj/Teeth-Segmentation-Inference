# 🦷 Teeth Segmentation Inference Pipeline

This repository demonstrates a fully reproducible inference pipeline for 3D teeth segmentation using deep learning models (DGCNN, PointNet, PointNet++, and TGNet). It includes the complete workflow from data ingestion to 3D visualization, along with comparisons between Ground Truth (GT) and Predicted (Pred) meshes.

> **Note for Recruiters:** This project involved taking a legacy research codebase and re-engineering it to function in a modern production environment (Google Colab/T4 GPU) by fixing deprecated C++ dependencies and automating data pipelines.

## 🔎 Project Overview
* **Goal:** Automated segmentation of teeth from 3D intraoral scans.
* **Data Type:** 3D Point Clouds / Meshes (`.ply`, `.obj`).
* **Environment:** Google Colab (GPU-accelerated).

---

## 🔧 Technical Implementation & Fixes
*To successfully deploy these models, I modernized the original legacy codebase, which was incompatible with current PyTorch versions. Below are the key engineering challenges I resolved:*

### 1. Migrated Deprecated PyTorch C++ Extensions (CUDA)
* **The Challenge:** The original model relied on older PyTorch C++ bindings, specifically including `THC/THC.h`. This caused the critical compilation error:
  > `fatal error: THC/THC.h: No such file or directory`
* **The Solution:** I refactored the underlying C++ source files (`aggregation_cuda.cpp`, `grouping_cuda.cpp`, etc.) to remove dependencies on the deprecated `THC` library. I updated the code to use the modern **ATen** API and `torch/extension.h`, allowing the custom CUDA kernels to compile and run on modern T4 GPUs.

### 2. Engineered Dynamic Data Pipeline
* **The Challenge:** The original repository lacked a clear data ingestion strategy, relying on static paths and missing zip files.
* **The Solution:** I wrote a custom Python pipeline to securely authenticate and download specific datasets from Google Drive, unzip them, and programmatically restructure the directories into the format required by the inference engine (`data_obj_parent_directory`).

### 3. Automated Inference Metadata Generation
* **The Challenge:** The inference script failed at runtime because it expected a specific text file listing test cases, which was not provided in the source.
* **The Solution:** I implemented a pre-processing script that scans the downloaded data directory, sanitizes filenames, and dynamically generates the required split file (`base_name_test_fold.txt`) at runtime, ensuring the pipeline runs without manual intervention.

---

## 📊 Model Visualizations
Below are the visual difference maps for each deep learning model. These maps illustrate the comparison between the predicted segmentation and the ground truth.

### DGCNN
![DGCNN Difference Map](teeth_segmentation_ply_obj_png/dgcnn/ImageToStl.com_visual_difference_map_dgcnn.png)

### PointNet
![PointNet Difference Map](teeth_segmentation_ply_obj_png/pointnet/ImageToStl.com_visual_difference_map_pointnet.png)

### PointNet++
![PointNet++ Difference Map](teeth_segmentation_ply_obj_png/pointnetpp/ImageToStl.com_visual_difference_map_pointnetpp.png)

### TgNet
![TgNet Difference Map](teeth_segmentation_ply_obj_png/tgnet/ImageToStl.com_visual_difference_map_tgnet.png)

---

## 📂 Folder Structure
The `teeth_segmentation_ply_obj_png` folder contains:
* **`.obj` Files:** The raw 3D mesh inputs (e.g., `01E1XHG8_upper.obj`).
* **`_gt_colored.ply`:** Ground Truth segmentation labels (colored).
* **`_pr_colored.ply`:** Model Predicted segmentation labels (colored).
* **Difference Maps:** Files showing the difference between Ground Truth and Prediction.

## 🛠 Visualization Tools
To view the raw `.ply` or `.obj` files, you can use the following tools:
* **[ImageToStl (Online Viewer)](https://imagetostl.com/view-ply-online)** - *Recommended for quick viewing in the browser.*
* [MeshLab](https://www.meshlab.net/)
* [CloudCompare](https://www.danielgm.net/cc/)
* [Open3D (Python)](http://www.open3d.org/)
