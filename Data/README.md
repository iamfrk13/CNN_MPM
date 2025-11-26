# Data (Not Included Due to Large File Size)

This folder is reserved for the sample raster datasets used in this project.  
The files listed below are **not included** in the repository because their size exceeds GitHub’s storage limits.

These rasters are generated during remote sensing based preprocessing using software QGIS 3.40.4 LTR after being downloaded from USGS Earth Explorer.

---

## 📁 Expected Files (Not Uploaded)

### **1. core_area_raster**
- Preprocessed Sentinel-2 MSI stack (9 bands)
- Clipped to the Reko Diq study area
- Resampled to 10 m resolution
- Input for `cnn_core.py`

### **2. core_ratios**
- MSI + geological band ratios (iron oxide, clay, alteration indices)
- Total feature channels: 13
- Input for `cnn_core_ratios.py`

### **3. core_pca_mnf**
- MSI + PCA + MNF components
- Noise-reduced feature stack
- Total feature channels: 13
- Input for `cnn_core_pca_mnf.py`

---

## 🔄 How to Regenerate These Files

All three datasets can be recreated using:
Script/Preprocessing.py


This script:

1. Downloads or reads Sentinel-2 imagery  
2. Clips to the study area  
3. Computes band ratios  
4. Performs PCA and MNF  
5. Creates the feature stacks listed above

---

## 🌐 Original Data Source

Full Sentinel-2 data can be downloaded from:

https://earthexplorer.usgs.gov/

---

## 📝 Note

These files are intentionally excluded to keep the repository light and within GitHub’s storage limits.  
All processing steps are fully documented in:

- `README.md`
- `METHODS.md`
- `Script/Preprocessing.py`

---
