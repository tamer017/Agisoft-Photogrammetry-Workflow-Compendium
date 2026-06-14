# Agisoft Photogrammetry Workflow Compendium

> **Full Python-automated UAV 3D reconstruction pipeline: SfM alignment, MVS dense point cloud, mesh reconstruction, orthomosaic, DEM, and multispectral NDVI mapping via the Agisoft Metashape API.**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Metashape](https://img.shields.io/badge/Agisoft-Metashape_API-green.svg)](https://www.agisoft.com/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-blue.svg)](https://opencv.org/)

---

## Overview

This project documents and automates a complete **UAV photogrammetry pipeline** using the Agisoft Metashape Python API. It covers the entire workflow from raw drone images to publication-ready 3D products: point clouds, textured meshes, orthomosaics, Digital Elevation Models (DEMs), and multispectral vegetation indices.

Designed for precision agriculture, infrastructure inspection, and geospatial research applications.

---

## Full Pipeline

```
Raw UAV Images (RGB + Multispectral)
           │
   ┌─────────┼─────────┐
   │  Image Alignment (SfM)    │
   │  SIFT feature detection   │
   │  Bundle adjustment        │
   └─────────┬─────────┘
           │
   ┌─────────┼─────────┐
   │  Dense Point Cloud (MVS)  │
   │  Multi-View Stereo        │
   └─────────┬─────────┘
           │
   ┌─────┼────┐
   │         │      │
 Mesh   Orthomosaic  DEM
(Poisson) (GeoTIFF) (DTM/DSM)
           │
   NDVI / Multispectral Maps
```

---

## Modules

### 1. Structure-from-Motion (SfM) Image Alignment
- Feature detection and matching: **SIFT vs. ORB systematic benchmark**
- Keypoint matching with ratio test filtering
- Bundle adjustment for camera pose estimation and sparse point cloud
- Ground Control Point (GCP) integration for georeferencing accuracy

### 2. Multi-View Stereo (MVS) Dense Reconstruction
- Dense depth map computation from calibrated camera positions
- Point cloud density: Ultra / High / Medium / Low quality modes
- Automatic noise filtering and outlier removal

### 3. Mesh Reconstruction
- **Poisson surface reconstruction** for watertight 3D meshes
- Texture mapping from original RGB images
- LOD (Level of Detail) mesh decimation for web/AR export

### 4. Orthomosaic & DEM Export
- **Orthomosaic**: orthorectified GeoTIFF with centimeter-level resolution
- **DSM** (Digital Surface Model): includes vegetation/structures
- **DTM** (Digital Terrain Model): bare-earth after filtering
- Coordinate reference system (CRS) assignment and reprojection

### 5. Multispectral NDVI Mapping
```python
# MicaSense RedEdge 5-band imagery
# Bands: Blue(475nm), Green(560nm), Red(668nm), RedEdge(717nm), NIR(840nm)
NDVI = (NIR - Red) / (NIR + Red)

# Radiometric calibration from reflectance panels
calibrated = raw_band / dark_current * reflectance_factor
```
- Radiometric calibration from MicaSense reflectance panel images
- Per-band vignetting and lens distortion correction
- NDVI, NDRE, GNDVI indices for crop health monitoring

### 6. Thermal Inspection
- Radiometric TIFF processing for infrastructure thermal anomaly detection
- Temperature mapping with emissivity correction

---

## Feature Matching Benchmark

| Detector | Keypoints | Match Rate | Speed |
|---|---|---|---|
| **SIFT** | ~3,200/image | 78% | Slower |
| **ORB** | ~1,800/image | 61% | 5× faster |

SIFT recommended for high-accuracy reconstruction; ORB for rapid preview workflows.

---

## Installation

```bash
git clone https://github.com/tamer017/Agisoft-Photogrammetry-Workflow-Compendium.git
cd Agisoft-Photogrammetry-Workflow-Compendium
pip install opencv-python numpy matplotlib pillow rasterio
# Agisoft Metashape Professional license required for API access
```

---

## Skills & Concepts

`UAV Photogrammetry` `Structure-from-Motion` `Multi-View Stereo` `GIS` `NDVI` `Remote Sensing` `Agisoft Metashape` `OpenCV` `SIFT` `ORB` `Point Cloud Processing` `Orthomosaic` `DEM` `Precision Agriculture`

---

## Author

**Ahmed Tamer Assy** — [GitHub](https://github.com/tamer017) | Machine Learning Researcher @ Volkswagen AG
