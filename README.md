# Teeth Segmentation Inference

This repository contains inference results for 3D teeth segmentation. It includes ground truth (GT) and predicted (Pred) 3D models for upper and lower jaws.

## Project Overview
* **Goal:** Automated segmentation of teeth from 3D intraoral scans.
* **Data Type:** 3D Point Clouds / Meshes (`.ply`, `.obj`).

## Folder Structure
The `teeth_segmentation_ply_obj_png` folder contains:
* **`.obj` Files:** The raw 3D mesh inputs (e.g., `01E1XHG8_upper.obj`).
* **`_gt_colored.ply`:** Ground Truth segmentation labels (colored).
* **`_pr_colored.ply`:** Model Predicted segmentation labels (colored).
* **Difference Maps:** Files showing the difference between Ground Truth and Prediction.

## Visualization
To view these files locally, you can use software like:
* MeshLab
* CloudCompare
* Open3D (Python)