# Single-Cell RNA-seq Data Analysis of Bone Marrow

## Introduction and Methodology

This notebook performs a comprehensive single-cell RNA-seq data analysis on bone marrow samples. The process involves:

1.  **Data Loading**: An h5ad file (`bone_marrow.h5ad`) is loaded into an AnnData object.
2.  **Quality Control (QC)**: Cells and genes are filtered based on expression counts, mitochondrial, ribosomal, and hemoglobin content. Doublets are detected using Scrublet.
3.  **Normalization**: Raw counts are normalized and `log1p` transformed.
4.  **Highly Variable Genes**: Top 1000 highly variable genes are identified.
5.  **Dimensionality Reduction**: Principal Component Analysis (PCA) and Uniform Manifold Approximation and Projection (UMAP) are used to reduce data dimensions for visualization.
6.  **Clustering**: Leiden clustering is applied to group cells into distinct populations.
7.  **Cell Type Annotation**: `decoupler` is used with PanglaoDB markers to infer and assign cell type labels to clusters.

## Key Findings and Interpretations

### Identified Cell Types
Neutrophils, B cells naive, T cells, Plasma cells, Gamma delta T cells, Dendritic cells, and Platelets.

### Assessment of Tissue Source
The dataset's cellular composition does not fully align with a typical healthy bone marrow sample. High proportions of T cells, Gamma delta T cells, Plasma cells, and Dendritic cells, coupled with the absence of key hematopoietic progenitor populations, suggest the sample is likely an immune-enriched compartment, a peripheral blood mononuclear cell (PBMC) sample, or reflects an active immune response.

### Patient Health Status
The patient is likely infected or experiencing a strong inflammatory response. The high abundance of active immune cells, including T cells (35.75%), Gamma delta T cells (17.11%), Neutrophils (15.91%), Plasma cells (14.60%), and Dendritic cells (10.38%), indicates a highly engaged immune system fighting a pathogen or significant inflammation, consistent with the dataset's origin from COVID-19 patients.

## How to Run the Notebook

1.  Open in Google Colab.
2.  Run all installation commands (`!pip install ...`) first.
3.  Execute all cells sequentially using 'Runtime' -> 'Run all'.
4.  Review outputs for data processing and analysis steps.

### Insights or Next Steps

*   The workflow can be applied to other scRNA-seq datasets from infectious/inflammatory conditions.
*   Further in-depth analysis of functional states and interactions of identified immune subsets (T cells, Gamma delta T cells, Plasma cells) could provide crucial insights into immune mechanisms during infection/inflammation.
