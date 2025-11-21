# HackBio-StageTwo
# Single-Cell RNA Sequencing Data Analysis: Bone Marrow Immunophenotyping

This notebook demonstrates a comprehensive analysis workflow for single-cell RNA sequencing (scRNA-seq) data, focusing on immunophenotyping of a bone marrow sample from patients. The analysis covers data loading, quality control, normalization, dimensionality reduction, clustering, and cell type annotation using external marker gene databases.

## What Was Done:

1.  **Installation of Libraries**: Essential bioinformatics and data science libraries such as `scanpy`, `anndata`, `igraph`, `celltypist`, `decoupler`, and `fa2-modified` were installed.
2.  **Data Loading**: A bone marrow scRNA-seq dataset (`bone_marrow.h5ad`) was loaded into an `AnnData` object.
3.  **Quality Control (QC)**:
    *   Mitochondrial (MT), ribosomal (RIBO), and hemoglobin (HB) genes were identified.
    *   QC metrics (number of genes, total counts, percentage of MT/RIBO/HB counts) were calculated.
    *   Cells with very low gene counts (min_genes < 1000) and genes expressed in too few cells (min_cells < 1000) were filtered out.
    *   Cells with high ribosomal contamination (pct_counts_RIBO > 10) were removed.
    *   Doublets were detected using Scrublet.
4.  **Normalization and Feature Selection**:
    *   Data was normalized to median total counts and log-transformed.
    *   Highly variable genes (top 1000) were identified for downstream analysis.
5.  **Dimensionality Reduction**:
    *   Principal Component Analysis (PCA) was performed.
    *   Uniform Manifold Approximation and Projection (UMAP) was used for visualization.
6.  **Clustering**: The Leiden algorithm was applied at various resolutions (`0.02`, `0.5`, `2`) to identify distinct cell clusters.
7.  **Cell Type Annotation**:
    *   The `decoupler` library was used with the PanglaoDB human marker gene database to infer cell types based on gene expression.
    *   Clusters were annotated by ranking cell type scores and mapping the most enriched cell type to each cluster.

## What Was Found:

*   **Identified Cell Types**: The primary cell types identified in the dataset were **T cells**, **Dendritic cells**, and **Plasma cells**.
*   **Cell Type Frequencies**: The relative frequencies were approximately:
    *   T cells: 62.37%
    *   Dendritic cells: 24.81%
    *   Plasma cells: 12.80%
*   **Tissue Source Consistency**: The cellular composition (high T cells, high dendritic cells, and absence of typical bone marrow precursors) suggests the sample is **not a representative healthy whole bone marrow sample**. It is more consistent with an immune-enriched compartment or peripheral blood mononuclear cells (PBMCs).
*   **Patient Health Status**: Based on the elevated proportions of T cells, dendritic cells, and plasma cells, the patient is likely **infected or experiencing an active inflammatory immune response**, rather than being healthy.

## How to Run This Notebook:

1.  **Open in Google Colab**: Upload or open this `.ipynb` file in Google Colab.
2.  **Run All Cells**: Go to `Runtime > Run all` to execute all the code cells sequentially. The notebook will perform all installations, data processing, and analysis steps.
3.  **Review Outputs**: Examine the generated plots and printed information in the output cells to follow the analysis and understand the findings.

## Discussion and Interpretation:

*   **Biological Roles**: The notebook provides concise biological roles for Dendritic cells, Plasma cells, and T cells in the context of immunity.
*   **Bone Marrow Identity**: A detailed justification is provided for why the sample is unlikely to be a typical healthy bone marrow, highlighting the absence of hematopoietic stem cells, myeloid, and erythroid precursors, and the dominance of immune cell populations.
*   **Patient Status**: An assessment is made that the patient is likely infected or in an inflammatory state, drawing conclusions from the unexpectedly high frequencies of activated immune cells compared to a healthy state.
