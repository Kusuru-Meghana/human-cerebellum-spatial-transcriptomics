# Spatial Transcriptomics Analysis of Human Cerebellum (10x Visium)
## Overview

In this project, I analyze 10x Genomics Visium spatial transcriptomics data from human cerebellum tissue to study how gene expression varies across space. The goal is to understand whether transcriptional patterns alone can recover meaningful tissue organization and to identify genes that define spatial regions within the cerebellum.

This project focuses on combining careful quality control, expression-based clustering, and spatial validation to draw biologically interpretable conclusions from spatial transcriptomics data.

## Goal

Identify spatially coherent transcriptional domains in human cerebellum tissue and characterize the gene expression programs underlying these regions.

## Key Question

Can gene expression patterns in spatial transcriptomics data recover biologically meaningful and spatially coherent tissue regions?

## Dataset

- Platform: 10x Genomics Visium

- Tissue: Human Cerebellum

- Data includes:

  - Gene expression counts measured per spatial spot

  - Spatial coordinates mapping each spot to its physical location in the tissue

Raw data are publicly available from 10x Genomics and are not included in this repository due to file size constraints.


## Analysis Approach

The analysis follows a standard but carefully controlled spatial transcriptomics workflow:

1. Data loading and spatial integration
Gene expression matrices and spatial metadata were loaded and combined into a single AnnData object, linking transcriptional profiles with physical tissue coordinates.

2. Quality control and filtering
Low-quality spots were identified using mitochondrial gene fraction, library size, and gene complexity metrics. Spatial visualization of QC metrics was used to detect damaged or low-quality tissue regions, which were excluded from downstream analysis.

3. Expression-only clustering
Gene expression data were normalized, log-transformed, and reduced using highly variable gene selection and PCA. Leiden clustering was performed using only gene expression information, without incorporating spatial coordinates.

4. Spatial coherence validation
Expression-derived clusters were projected back onto tissue coordinates to assess whether transcriptional similarity corresponded to spatially contiguous regions.

5. Spatially informed clustering
Spatial neighborhood graphs were constructed to perform clustering that explicitly incorporates physical proximity between spots, allowing comparison with expression-only results.

6. Marker gene analysis
Differential expression analysis was used to identify genes enriched in each spatial domain, providing insight into the transcriptional programs defining different tissue regions.

## Key Results

- Expression-based clustering alone recovered spatially coherent regions, indicating that transcriptional similarity reflects underlying tissue organization.

- Incorporating spatial neighborhood information produced smoother and more contiguous domains, refining regional boundaries.

- Distinct sets of marker genes were identified for each spatial domain, highlighting transcriptional heterogeneity across the cerebellum.

## Biological Interpretation

The results show that human cerebellum tissue is organized into spatial domains with distinct gene expression profiles. Importantly, this structure can be recovered using gene expression alone, demonstrating that spatial organization is encoded in transcriptional programs. Spatial information further sharpens domain boundaries and reduces local noise, improving interpretability.

## Tools Used

- Python

- Scanpy

- Squidpy

- NumPy, Pandas

- Matplotlib

## Repository Structure
```
notebooks/        Full analysis workflow
results/          Figures and result tables
data/             Instructions for data access
environment.yml   Reproducible software environment
```

## Reproducibility

The complete analysis is documented in:
``` notebooks/spatial_analysis.ipynb ```


An environment specification is provided to support reproducibility.

## Author
Meghana Kusuru
meghanak@udel.edu
Interested in computational biology, genomics, and spatial omics research roles

