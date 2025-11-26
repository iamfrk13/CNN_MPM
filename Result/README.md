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

- **core_area_raster_aligned.tif** — Sentinel-2 RGB composite representing the Reko Diq study area.
- **gossan_composite_raster_float.tif** — Composite image showing band-ratio layers used as input for CNN.
- **ferric_B4_div_B3_norm.tif** — ferric iron map generation using B4/B3.
- **ferricoxide_B11_div_B08_norm.tif** — ferric oxide map generation using B11/B8a.
- **ferrous_combined_norm.tif** — ferrous iron map generation using (B12/B8a + B3/B4).
- **hydroxyl_B11_div_B12_norm.tif** — ferric oxide map generation using B11/B12.
- **stacked_ratios_aligned.tif** — All band ratio maps stacked.
- **pca_1_2_stack_aligned.tif** — PCA-transformed component visualization from Sentinel-2 data.
- **mnf_1_2_stack_aligned.tif** — MNF-transformed imagery showing directional noise-filtered components.
- **core_area.shp** — Shape file of the Reko Diq study area.
- 

All visual products correspond to the Reko Diq Porphyry Cu–Au deposit and were derived from Sentinel-2 Level-2A imagery using the workflow described in the manuscript.
