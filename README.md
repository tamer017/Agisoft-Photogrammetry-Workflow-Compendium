# Agisoft Photogrammetry Workflow Compendium

> A comprehensive research compendium benchmarking **SIFT vs. ORB feature detectors** for UAV-based 3D reconstruction using the Agisoft Metashape Python API.

[![Tool](https://img.shields.io/badge/Tool-Agisoft%20Metashape-blue?style=flat-square)](https://www.agisoft.com/)
[![Language](https://img.shields.io/badge/Language-Python%2FJupyter-green?style=flat-square)]()
[![Domain](https://img.shields.io/badge/Domain-UAV%20Photogrammetry-orange?style=flat-square)]()

---

## Overview

This project provides a **rigorous, end-to-end documentation and automation compendium** for UAV-based photogrammetric 3D reconstruction workflows. It leverages the **Agisoft Metashape Python API** to automate multi-stage pipelines — from raw image ingestion through dense point cloud generation, mesh reconstruction, and orthomosaic export — while conducting a systematic **SIFT vs. ORB feature detector benchmark** to quantify trade-offs in accuracy, processing time, and output density.

The project targets aerial survey practitioners, GIS analysts, and remote sensing researchers who need reproducible, script-driven photogrammetry pipelines for precision agriculture, infrastructure inspection, and terrain modeling applications.

---

## Photogrammetry Pipeline

```
[UAV Image Acquisition]
  Raw JPEG/TIFF images + GPS EXIF metadata
              |
              v
  [1. Image Alignment]
  Feature detection: SIFT or ORB
  Feature matching across overlapping images
  Bundle adjustment → sparse point cloud + camera poses
              |
              v
  [2. Dense Point Cloud Generation]
  Multi-View Stereo (MVS) depth estimation
  Depth map fusion → dense 3D point cloud
              |
              v
  [3. Mesh Reconstruction]
  Poisson surface reconstruction
  Texture projection from source images
              |
              v
  [4. Export Products]
  ├── Dense Point Cloud (.las / .ply)
  ├── 3D Mesh (.obj / .fbx)
  ├── Orthomosaic GeoTIFF (cm-resolution)
  └── Digital Elevation Model (DEM)
```

---

## SIFT vs. ORB Benchmark

### Why This Comparison Matters

Feature detector choice is the single most impactful decision in photogrammetric pipeline design:
- **SIFT** (Scale-Invariant Feature Transform): High accuracy, rotation/scale invariant, computationally expensive, patented (open-source via OpenCV)
- **ORB** (Oriented FAST + Rotated BRIEF): Real-time capable, license-free, lower accuracy on low-texture scenes

### Benchmark Dimensions

| Metric | SIFT | ORB |
|---|---|---|
| Keypoints detected | High density | Moderate density |
| Matching accuracy | High (ratio test) | Moderate (Hamming distance) |
| Processing time | Slow | Fast (~10× speedup) |
| Dense cloud density | Higher | Lower |
| Robustness (low texture) | Better | Weaker |
| Use case fit | Precision mapping | Real-time / edge |

> Full quantitative results with point cloud density metrics, alignment RMS, and timing benchmarks are available in the Jupyter notebooks.

---

## Multispectral & Thermal Extensions

The compendium also documents workflows for **multispectral and thermal imaging** sensors:
- **Multispectral:** NDVI map generation from 5-band (Blue, Green, Red, RedEdge, NIR) imagery for precision agriculture
- **Thermal:** Radiometric calibration of FLIR sensor data for building envelope inspection and solar panel fault detection

---

## Metashape Python API Automation

```python
import Metashape

doc = Metashape.Document()
chunk = doc.addChunk()

# Load images
chunk.addPhotos(image_list)

# Align photos (feature detection + matching)
chunk.matchPhotos(keypoint_limit=40000, tiepoint_limit=4000)
chunk.alignCameras()

# Dense reconstruction
chunk.buildDepthMaps(quality=Metashape.MediumQuality)
chunk.buildDenseCloud()

# Export orthomosaic
chunk.buildOrthomosaic()
chunk.exportRaster('orthomosaic.tif', 
                   source_data=Metashape.OrthomosaicData)
```

---

## Project Structure

```
Agisoft-Photogrammetry-Workflow-Compendium/
├── notebooks/
│   ├── 01_alignment_benchmark.ipynb    # SIFT vs ORB comparison
│   ├── 02_dense_cloud_analysis.ipynb   # Point cloud density metrics
│   └── 03_multispectral_ndvi.ipynb      # NDVI map generation
├── scripts/
│   ├── full_pipeline.py               # End-to-end Metashape automation
│   └── export_products.py             # Orthomosaic/DEM export utilities
└── results/                           # Benchmark outputs and figures
```

---

## Getting Started

### Prerequisites
- [Agisoft Metashape Professional](https://www.agisoft.com/downloads/installer/) (license required)
- Python 3.8+ with Metashape Python module
- OpenCV (`pip install opencv-python`)
- Jupyter Notebook

```bash
git clone https://github.com/tamer017/Agisoft-Photogrammetry-Workflow-Compendium.git
cd Agisoft-Photogrammetry-Workflow-Compendium
pip install opencv-python numpy pandas matplotlib jupyter
jupyter notebook notebooks/01_alignment_benchmark.ipynb
```

---

## Skills Demonstrated

- **Photogrammetry:** SfM pipeline, MVS dense reconstruction, bundle adjustment, GCP integration
- **Computer Vision:** SIFT, ORB, feature matching, homography estimation
- **Remote Sensing:** UAV survey design, orthomosaic generation, DEM production, NDVI analysis
- **Automation:** Agisoft Metashape Python API, batch processing, reproducible workflows
- **Geospatial:** GeoTIFF export, coordinate reference systems (CRS), point cloud processing

---

## References

- [Agisoft Metashape Python API Reference](https://www.agisoft.com/pdf/metashape_python_api_2_0_0.pdf)
- Lowe, D.G. (2004). *Distinctive Image Features from Scale-Invariant Keypoints*. IJCV.
- Rublee et al. (2011). *ORB: An efficient alternative to SIFT or SURF*. ICCV.
