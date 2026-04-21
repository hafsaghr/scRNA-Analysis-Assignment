# Single-Cell RNA Sequencing (scRNA-seq) Analysis Pipeline

## Overview
This repository contains a modular computational pipeline for analyzing single-cell RNA sequencing (scRNA-seq) data using Python. The workflow demonstrates the transition from raw digital expression matrices to the identification of transcriptionally distinct cell populations.

The project is structured into three distinct analytical phases to ensure reproducibility and clean data management:
1. **01_scrna-preprocessing-10x** — Data ingestion and statistical quality control.
2. **02_basic-scrna-tutorial** — Dimensionality reduction, visualization, and unsupervised clustering.
3. **03_anndata-tutorial** — Implementation and manipulation of the AnnData object standard.

---

## Technical Methodology

### Phase 1: Upstream Processing & Quality Control
The initial phase focuses on loading pre-computed 10X Genomics count matrices (3k PBMCs) and applying strict quality control measures to ensure downstream analysis is not affected by technical artifacts.
* **Data Ingestion:** Utilizing the Scanpy library to load sparse `.mtx` feature-barcode matrices.
* **Cell & Gene Filtering:** Removing low-quality droplets (cells with < 200 expressed genes) and rare transcripts (genes expressed in < 3 cells).
* **Mitochondrial Filtering:** Excluding damaged or dying cells by filtering out barcodes with a high percentage of mitochondrial gene expression (>5%).

### Phase 2: Downstream Analysis & Clustering
This phase leverages the Scanpy ecosystem to extract biological signals from the cleaned dataset.
* **Normalization:** Log-transformation and scaling of raw counts to ensure comparability across cells.
* **Feature Selection:** Identification of Highly Variable Genes (HVGs) to reduce background noise.
* **Dimensionality Reduction:** Execution of Principal Component Analysis (PCA) to capture overarching variance, followed by Uniform Manifold Approximation and Projection (UMAP) for 2D visualization.
* **Clustering:** Application of the Leiden community detection algorithm to group cells based on transcriptional similarities.

### Phase 3: Data Management with AnnData
A demonstration of the `AnnData` structure, the core framework used in single-cell Python ecosystems.
* **Structure Visualization:** Exploring the `n_obs` (cells) and `n_vars` (genes) multi-dimensional arrays.
* **Metadata Integration:** Managing observational cell metadata (`.obs`) and variable gene annotations (`.var`).
* **Slicing Operations:** Executing efficient subsetting queries on the dataset.

---

## Core Technologies
* **Language:** Python 3.x
* **Bioinformatics Libraries:** `scanpy`, `anndata`, `leidenalg`
* **Data Handling:** `pandas`, `numpy`
* **Visualization:** `matplotlib`
