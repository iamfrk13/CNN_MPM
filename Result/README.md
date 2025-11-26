# Results

This folder contains visual outputs generated during the preprocessing, training, and CNN-based mineral prospectivity mapping workflow.

## 📁 Figures
These images show model performance and training behavior:

- **pca_selection_plot.jpg** — Selection of pca components.
- **mnf_selection_plot.jpg** — Selection of mnf components.
- **CNN_Scratch.jpg** — Validation accuracy curves for scratch model using 9 MSI bands, 13 MSI + BR bands and 13 MSI + PCA + MNF bands respectively.
- **CNN_Augmented.jpg** — Validation accuracy curves for augmented model using 9 MSI bands, 13 MSI + BR bands and 13 MSI + PCA + MNF bands respectively.
- **CNN_Finetuned_Head.jpg** — Validation accuracy curves for finetuned head model using 9 MSI bands, 13 MSI + BR bands and 13 MSI + PCA + MNF bands respectively.
- **CNN_Finetuned_Final.jpg** — Validation accuracy curves for finetuned final model using 9 MSI bands, 13 MSI + BR bands and 13 MSI + PCA + MNF bands respectively.
- **paper_1_bar_graph.jpg** — Comparison of CNN-Based Models under different datasets and configurations.

## 📁 Maps
These are spatial outputs generated from the CNN models:

- **study area raster.jpg** — Sentinel-2 imagery clipped to study area (reko diq).
- **band_ratios_composite_labeled.jpg** — Final prospectivity map based on MSI-only model.
- **pca_1.jpg** — Final map using MSI + band ratios.
- **pca_2.jpg** — Final map using MSI + PCA + MNF.
- **mnf_stack.jpg** — Validation of predicted high-prospectivity zones using field data (optional).

All outputs correspond to the Reko Diq Porphyry Cu–Au system, generated from Sentinel-2 imagery.
