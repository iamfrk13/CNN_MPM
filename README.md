# CNN_MPM
## Convolutional Neural Network–Based Mineral Prospectivity Mapping Using Sentinel-2 Data
### Case Study: Reko Diq Porphyry Cu–Au Deposit, Pakistan

This repository contains code, preprocessing scripts, and supporting material for my research work:

**Khan, F., & Baig, S. (2025). Convolutional Neural Network-Based Deep Learning Approach for Mineral Prospectivity Mapping using Sentinel-2 Data: A Case Study of the Reko Diq Porphyry Cu–Au Deposit, Pakistan.**

---

## 📁 Repository Structure

CNN_MPM/
│
├── README.md
├── LICENSE
├── requirements.txt
│
├── preprocessing/
│   └── Preprocessing.py
│
├── models/
│   ├── cnn_core.py              (for 9 MSI bands)
│   ├── cnn_core_ratios.py       (for band ratios + MSI i.e. 13 bands)
│   ├── cnn_core_pca_mnf.py      (for PCA + MNF + MSI i.e. 13 bands)
│
├── data/
│   └── sample_tiles/
│
└── results/
    ├── figures/
    └── maps/
  

---

## ▶️ How to Run This Project (Anaconda Environment)

### 1. Install required libraries:
pip install -r requirements.txt


### 2. Run preprocessing:
python preprocessing/Preprocessing.py

### 3. Train and evaluate CNN models:

**MSI-based CNN**
python models/cnn_core.py

**MSI + Band Ratios**
python models/cnn_core_ratios.py

**MSI + PCA + MNF**
python models/cnn_core_pca_mnf.py


---

## 📦 Data Availability
Full Sentinel-2 data and generated training tiles are too large for GitHub.  
You can download Sentinel-2 imagery from USGS Earth Explorer:  
https://earthexplorer.usgs.gov/

Use the preprocessing script to recreate all training tiles.

---

## 📝 Citation
Please cite this work as:

**Khan, F., & Baig, S. (2025). Convolutional Neural Network-Based Deep Learning Approach for Mineral Prospectivity Mapping using Sentinel-2 Data: A Case Study of the Reko Diq Porphyry Cu–Au Deposit, Pakistan.**

---

## 📧 Contact
Author: **Feroz Khan**  
Email: **feroz_hallian@hotmail.com**

