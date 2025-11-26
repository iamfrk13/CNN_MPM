# METHODS — CNN-Based Mineral Prospectivity Mapping Using Sentinel-2 Data

This document describes the complete methodological workflow used in the research titled:

**“Convolutional Neural Network-Based Deep Learning Approach for Mineral Prospectivity Mapping using Sentinel-2 Data: A Case Study of the Reko Diq Porphyry Cu–Au Deposit, Pakistan.”**

It covers all steps from data acquisition to preprocessing, feature extraction, model training, and final prospectivity mapping.

---

# 1. Study Area
- Location: **Reko Diq Porphyry Cu–Au Deposit**, Chagai District, Balochistan, Pakistan  
- Geological significance: One of the world’s largest undeveloped Cu–Au resources  
- Remote sensing relevance: Host rocks, alteration zones, and gossan signatures detectable via Sentinel-2 MSI multispectral features.

---

# 2. Data Acquisition
- Source: **USGS EarthExplorer**
- Dataset: **Sentinel-2 Level-2A multispectral imagery**
- Bands used:
  - 9 MSI bands: B2, B3, B4, B8 (10 m), B5, B6, B7, B8A, B12 (20 m)
- Acquisition filters:
  - Cloud cover < 5%
  - Seasonally stable imagery
  - Complete coverage of alteration zone geometry

---

# 3. Preprocessing Workflow

###  3.1 Atmospheric Correction
- "Image is already atmospherically corrected (Level-2A). Additional reflectance scaling applied."

###  3.2 Spatial Resolution Standardization
- Resampled 20 m bands to **10 m** using bilinear interpolation  
- Ensures uniform pixel size across all MSI channels

###  3.3 Clipping to Study Area
- Masked imagery using the Reko Diq AOI polygon  
- Exported as analysis-ready georeferenced mosaic

###  3.4 Dataset Tiling (Patch Extraction)
- The final labeled gossan raster and all feature stacks (MSI, band ratios, PCA, MNF) were tiled into fixed-size image patches for CNN training. The tiling process used the following workflow:

- Tile size: 64 × 64 pixels
- Overlap: 50% overlap in both x and y directions
- Input stacks tiled:
- MSI (core)
- MSI + Band Ratios
- MSI + PCA + MNF
- Combined stacks (total 8 different inputs)

#### Label raster: 3 classes
- 0 = None (Background)
- 1 = Weak gossan signal
- 2 = Strong gossan signal

#### Tile classification rules:
- A tile is labeled “strong” if ≥ 12% of its pixels belong to class 2
- A tile is labeled “weak” if ≥ 5% of its pixels belong to class 1
- Otherwise, the tile is labeled “none”
- All input rasters and the label raster were tiled in perfect alignment so each 64×64 tile had a matching label tile.

#### Train/validation/test split:
- 70% training
- 15% validation
- 15% testing

- Performed separately for each label class to maintain balance.
- Balanced dataset creation:
- Each class (none, weak, strong) was shuffled and split independently, resulting in balanced subsets for training, validation, and testing.

Complete preprocessing code:  
File: `Script/Preprocessing.py`

---

# 4. Feature Maps

Three feature sets were prepared:

---

## 4.1 MSI (Multispectral Bands Only)
- 9-band MSI stack  
- Captures raw spectral characteristics  
- Input shape: `64 × 64 × 9`

---

## 4.2 MSI + Band Ratios (13 Bands)
Classical geological ratios for clay, iron, and alteration mapping:
- Prepared by Remote Sensing based analysis using QGIS 3.40.4 LTR

Examples:
- (B4/B2), (B11/B8A), (B12/B8), Clay–Iron indices

Final stack:
- 9 MSI bands  
- + 4 band ratios  
- = **13 total channels**

---

## 4.3 MSI + PCA + MNF (13 Components)
Dimensionality reduction and noise filtering:
- Prepared by Remote Sensing based analysis using QGIS 3.40.4 LTR

### ✔ PCA
- Computed on MSI stack  
- Top 2 components selected based on explained variance  
- Selection curve:  
  `results/figures/pca_selection_plot.jpg`

### ✔ MNF
- Multivariate Noise Fraction transformation  
- Top 2 components selected based on SNR/eigenvalues  
- Selection curve:  
  `results/figures/mnf_selection_plot.jpg`

Final stack:
- 9 MSI + PCA + MNF = **13 channels**

---

# 5. CNN Model Architectures

Three CNN pipelines were trained:

---

## 5.1 CNN Core (MSI only)
File: `Script/cnn_core.py`

- Input: 9 MSI bands  
- Architecture:
  - Conv2D → ReLU → MaxPool  
  - Conv2D → ReLU → MaxPool  
  - Dense → Dropout  
  - Sigmoid/Softmax output  

---

## 5.2 CNN Core + Band Ratios
File: `Script/cnn_core_ratios.py`

- Input: 13 MSI+ratio channels  
- Same architecture  
- Band ratios enhance geological contrast

---

## 5.3 CNN Core + PCA + MNF
File: `Script/cnn_core_pca_mnf.py`

- Input: 13 MSI+PCA+MNF channels  
- PCA/MNF reduce noise and highlight alteration boundaries

---

# 6. Training Strategy

Each CNN was trained in four configurations:

### 1) Scratch Model  
Random initialization, no augmentation.

### 2) Augmented Model  
Augmentations:
- Rotation  
- Horizontal/vertical flipping  
- Zoom    

### 3) Finetuned Head  
Only dense layers of ResNet50 updated.

### 4) Fully Finetuned  
Last three layers from CNN backbone of ResNet50 unfrozen and retrained.

Validation accuracy curves:

- `results/figures/CNN_Scratch.jpg`
- `results/figures/CNN_Augmented.jpg`
- `results/figures/CNN_Finetuned_Head.jpg`
- `results/figures/CNN_Finetuned_Final.jpg`

Comparison:  
`results/figures/paper_1_bar_graph.jpg`

---

All intermediate and final maps are available in:  
`results/maps/`

---

# 7. Reproducibility

This repository includes:

- Preprocessing code → `Script/Preprocessing.py`  
- Feature stacks (generated by scripts)  
- CNN model scripts → `/Script/`  
- All figures & maps → `/results/`  
- Dependencies → `requirements.txt`  
- Execution instructions → `README.md`  
- Licensing → MIT license

The workflow is **fully reproducible** using public Sentinel-2 data.

---

# 📘 End of METHODS.md
