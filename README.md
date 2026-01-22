# Teeth Segmentation Inference

This repository contains inference results for 3D teeth segmentation. It includes ground truth (GT) and predicted (Pred) 3D models for upper and lower jaws.

## Project Overview
* **Goal:** Automated segmentation of teeth from 3D intraoral scans.
* **Data Type:** 3D Point Clouds / Meshes (`.ply`, `.obj`).

## Model Visualizations
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

## Folder Structure
The `teeth_segmentation_ply_obj_png` folder contains:
* **`.obj` Files:** The raw 3D mesh inputs (e.g., `01E1XHG8_upper.obj`).
* **`_gt_colored.ply`:** Ground Truth segmentation labels (colored).
* **`_pr_colored.ply`:** Model Predicted segmentation labels (colored).
* **Difference Maps:** Files showing the difference between Ground Truth and Prediction.

## Visualization Tools
To view the raw `.ply` or `.obj` files locally, you can use software like:
* [MeshLab](https://www.meshlab.net/)
* [CloudCompare](https://www.danielgm.net/cc/)
* [Open3D (Python)](http://www.open3d.org/)
