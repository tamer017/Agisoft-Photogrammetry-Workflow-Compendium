# Agisoft Photogrammetry Knowledge Compendium

> **Full Python-automated UAV 3D reconstruction pipeline: SfM alignment, MVS dense point cloud, mesh reconstruction, orthomosaic, DEM, and multispectral NDVI mapping via the Agisoft Metashape API.**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Metashape](https://img.shields.io/badge/Agisoft-Metashape_API-green.svg)](https://www.agisoft.com/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.x-blue.svg)](https://opencv.org/)

---

This repository serves as a comprehensive resource for documenting and standardizing the workflows and processing steps involved in UAV-based photogrammetry using **Agisoft Metashape**. It is designed to offer a transparent, reproducible, and detailed guide to photogrammetric processing—from the initial stages of image import and EXIF data handling, through image alignment, point cloud generation, and mesh creation, to the production of orthophotos and digital elevation models (DEMs).

By consolidating and expanding upon the standard procedures found in commercial photogrammetry software, this compendium aims to bridge the gap between proprietary workflows and academic research needs. The repository provides a step-by-step guide that not only clarifies each processing phase but also emphasizes reproducibility and accuracy—key factors for research applications such as plant disease analysis and remote sensing.

**Key Objectives:**

- **Comprehensive Documentation:** Detailed guides cover every stage of the photogrammetric process, including image pre-processing, data alignment, the creation of sparse and dense point clouds, and the generation of high-quality 3D models.
- **Reproducibility & Transparency:** By outlining clear, replicable workflows, this compendium addresses common gaps in the official documentation of commercial photogrammetry tools, fostering trust and verification in scientific studies.
- **Optimization Strategies:** The repository explores alternative processing techniques and algorithms—such as advanced feature matching and Semi-Global Matching (SGM)—that enhance data quality and improve processing efficiency.
- **Research-Driven Applications:** Special focus is placed on methodologies that have been successfully applied to plant disease studies and other research domains, ensuring that the documented workflows meet rigorous academic and practical standards.

**Note:** This repository is a work in progress. As photogrammetric techniques continue to evolve and new algorithms and processing steps emerge, not every cutting-edge method is currently covered. The steps detailed here represent a robust framework that will be expanded and refined over time. We welcome suggestions, contributions, and additions to help integrate the latest techniques and improve the overall scope of this compendium.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Documentation](#documentation)
4. [Getting Started](#getting-started)
5. [Contributing](#contributing)
6. [Contact](#contact)

---

## Project Overview

### Objectives
- **Document Key Processing Steps**: Provide a detailed guide for all major processes in Agisoft Metashape related to UAV data.
- **Address Gaps in Transparency**: Highlight and resolve steps that are under-documented in Metashape's official materials.
- **Recommend Alternatives**: Explore and suggest efficient algorithms or workflows.

### Expected Outcomes
- A well-documented repository featuring:
  - Comprehensive guides for Metashape processes.
  - Transparent alternatives for undocumented workflows.

---

## Repository Structure

```plaintext
Photogrammetry-master
├── .gitignore
├── README.md
├── algorithms
│   ├── feature_matching.md
│   └── SGM.md
├── data
│   ├── image.png
│   └── brandenburg_gate_images
│       └── jpg images
├── docs
│   ├── .gitkeep
│   ├── alignment.md
│   ├── camera.md
│   ├── DEM.md
│   ├── dense_cloud_generation.md
│   ├── exif_data_reading.md
│   ├── image_import.md
│   ├── mesh_creation.md
│   ├── orthomosiac_generation.md
│   ├── orthophoto_generation.md
│   ├── overall_workflow.md
│   ├── pixel_selection_strategies.md
│   ├── sparse_point_cloud.md
│   └── uav_multispectral_data.md
├── examples
│   └── .gitkeep
└── scripts
    ├── .gitkeep
    ├── feature_matching.ipynb
    └── orhomosaic_generation.ipynb
```

---

## Documentation

### Core Steps
- **Overall Workflow**: [overall_workflow.md](docs/overall_workflow.md) – High-level summary of the photogrammetry process.
- **Image Import**: [image_import.md](docs/image_import.md) – Guidance on importing UAV images into Metashape.
- **EXIF Data Reading**: [exif_data_reading.md](docs/exif_data_reading.md) – Verification and usage of metadata.
- **Alignment**: [alignment.md](docs/alignment.md) – Steps for aligning images to form a sparse point cloud.
- **Sparse Point Cloud**: [sparse_point_cloud.md](docs/sparse_point_cloud.md) – Details on generating the initial point cloud.
- **Dense Cloud Generation**: [dense_cloud_generation.md](docs/dense_cloud_generation.md) – Creating a detailed 3D point cloud.
- **Mesh Creation**: [mesh_creation.md](docs/mesh_creation.md) – Converting the dense cloud into a 3D mesh.
- **Orthophoto Generation**: [orthophoto_generation.md](docs/orthophoto_generation.md) – Creating georeferenced orthophotos.
- **Digital Elevation Model (DEM)**: [DEM.md](docs/DEM.md) – Steps to generate a DEM from processed data.

### Additional Documentation
- **Camera Details**: [camera.md](docs/camera.md) – Specifications of the multispectral camera.
- **UAV Multispectral Data**: [uav_multispectral_data.md](docs/uav_multispectral_data.md) – Key parameters of UAV-acquired data.
- **Pixel Selection Strategies**: [pixel_selection_strategies.md](docs/pixel_selection_strategies.md) – Approaches for selecting optimal pixels during processing.
- **Orthomosiac Generation**: [orthomosiac_generation.md](docs/orthomosiac_generation.md) – Alternative workflow for generating orthomosaics.

### Algorithms
- **Feature Matching**: [feature_matching.md](algorithms/feature_matching.md) – Discussion on feature matching techniques.
- **SGM (Semi-Global Matching)**: [SGM.md](algorithms/SGM.md) – Explanation and justification of the SGM algorithm.

---

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/tamer017/Agisoft-Photogrammetry-Workflow-Compendium.git
   cd Agisoft-Photogrammetry-Workflow-Compendium
   ```
2. **Explore the documentation:** Detailed instructions for each processing step are available in the `docs/` directory.
3. **Test the workflows:** Use the provided data in the `data/` folder and examples in the `examples/` directory.

---

## Contributing

We welcome contributions to enhance the repository!

1. Fork the repository.
2. Create a new feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make your changes and commit:
   ```bash
   git commit -m "Describe your changes here"
   ```
4. Push your branch to GitHub and create a pull request.

---

## Skills & Concepts

`UAV Photogrammetry` `Structure-from-Motion` `Multi-View Stereo` `GIS` `NDVI` `Remote Sensing` `Agisoft Metashape` `OpenCV` `SIFT` `ORB` `Point Cloud Processing` `Orthomosaic` `DEM` `Precision Agriculture`

---

## Contact

For questions, feedback, or collaboration, please reach out:
- **Ahmed Tamer Assy**: [ahmed.assy@stud.uni-goettingen.de](mailto:ahmed.assy@stud.uni-goettingen.de)
- **Supervisor Dr. Rene Heim**: [heim@ifz-goettingen.de](mailto:heim@ifz-goettingen.de)
