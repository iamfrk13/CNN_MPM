# Data

This folder contains sample raster inputs used in the mineral prospectivity workflow.  
These rasters represent the preprocessed and feature-enhanced input stacks that were used for generating CNN-based predictions.

---

## 📁 Files Included

### **1. core_area_raster**
- Preprocessed MSI stack clipped to the Reko Diq study area  
- Resampled to 10 m  
- Used as the base feature set for the `cnn_core.py` model  
- Contains 9 multispectral Sentinel-2 MSI bands

---

### **2. core_ratios**
- Composite raster including:
  - Multispectral MSI bands
  - Geological band ratios (iron‐oxide, clay, and alteration indicators)
- Total channels: **13**
- Used as input to `cnn_core_ratios.py`

---

### **3. core_pca_mnf**
- Feature-enhanced raster including:
  - MSI bands
  - PCA components
  - MNF components
- Noise-reduced representation of spectral alterations
- Total channels: **13**
- Used as input to `cnn_core_pca_mnf.py`

---

## 🔍 Notes

- The full-resolution Sentinel-2 dataset must be downloaded from  
  https://earthexplorer.usgs.gov/
- Complete preprocessing instructions are available in the repository root `README.md` and in `METHODS.md`.

---

