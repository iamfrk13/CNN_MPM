# Results

This folder contains visual outputs generated during preprocessing, dimensionality reduction, CNN model training, and mineral prospectivity mapping for the Reko Diq Porphyry Cu–Au system using Sentinel-2 data.

---

## 📁 Figures
These figures illustrate model behavior, component selection, and performance comparison.

- **pca_selection_plot.jpg** — Scree plot and variance contribution used to select optimal PCA components.
- **mnf_selection_plot.jpg** — Eigenvalue or SNR-based plot used to select optimal MNF components.

### CNN Model Performance (Accuracy Curves)
Each plot shows validation accuracy for three datasets:
- 9 MSI bands  
- 13 MSI + Band Ratios  
- 13 MSI + PCA + MNF  

- **CNN_Scratch.jpg** — Validation accuracy for scratch-trained CNN model.
- **CNN_Augmented.jpg** — Validation accuracy for the CNN model trained with data augmentation.
- **CNN_Finetuned_Head.jpg** — Validation accuracy for the head-finetuned CNN model.
- **CNN_Finetuned_Final.jpg** — Validation accuracy for the fully finetuned CNN model.

### Model Comparison
- **paper_1_bar_graph.jpg** — Comparison of overall model accuracies across different datasets and model configurations (scratch, augmented, head-finetuned, fully finetuned).

---

## 📁 Maps
These maps are spatial outputs derived from the CNN models and preprocessing workflow.

- **study area raster.jpg** — Sentinel-2 RGB composite representing the Reko Diq study area.
- **band_ratios_composite_labeled.jpg** — Composite image showing band-ratio layers used as input for CNN (not a prospectivity map).
- **pca_1.jpg** — PCA-transformed component visualization from Sentinel-2 data.
- **pca_2.jpg** — Additional visualization of PCA components (or second PCA output).
- **mnf_stack.jpg** — MNF-transformed imagery showing directional noise-filtered components.

All visual products correspond to the Reko Diq Porphyry Cu–Au deposit and were derived from Sentinel-2 Level-2A imagery using the workflow described in the manuscript.
