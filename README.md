# scRNAseq_analysis_Kameneva


scRNA-seq Analysis for Kameneva Lab PhD Selection

This repository contains the single-cell RNA sequencing (scRNA-seq) analysis pipeline performed by Adam Adonyi for the Kameneva Lab PhD selection process. The analysis focuses on identifying cell types, performing trajectory inference, and exploring gene expression changes across developmental stages in adrenal medulla-related populations.


# Overview

The goal of this project is to analyze scRNA-seq data from human adrenal gland development to identify key cell populations (Schwann Cell Precursors (SCPs), Chromaffin cells, and Sympathoblasts) and explore their differentiation trajectories. The pipeline includes quality control, clustering, annotation, trajectory analysis, and heatmap visualization.

# Dataset

The dataset used in this analysis was obtained from the Gene Expression Omnibus (GEO) database:

Accession Number: [GSE147821](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE147821)
Description: The dataset contains samples from different developmental stages (e.g., week 6 to week 14) of human adrenal gland development.
 Each sample name indicates the developmental stage (e.g., week8_001 corresponds to week 8 of development with internal ID 001). Some developmental stages have replicates.

 Pipeline Description

# The pipeline:

## Preprocessing :
Load .h5 files from the RAW.tar archive.
Generate Seurat objects for each sample and combine them into a single object.
Calculate mitochondrial content (percent.mt) for quality control.

## Quality Control :
Filter cells based on thresholds for nFeature_RNA, nCount_RNA, and percent.mt. (3xMAD)
Perform cell cycle scoring and regression. (Seurat)

## Clustering and Annotation :
Normalize data, perform PCA, and cluster cells using Seurat's standard pipeline.
Annotate clusters manually based on marker genes. [according to the reference](https://www.nature.com/articles/s41588-021-00818-x)

## Subsetting and Re-clustering :
Isolate SCPs, Chromaffin cells, and Sympathoblasts for detailed analysis.
Remove doublets, cell-cycle-related genes, and STAR-positive cells.

## Trajectory Analysis :
Perform trajectory inference using Slingshot.
Identify differentially expressed genes along pseudotime using tradeSeq.
Generate heatmaps to visualize gene expression changes during transitions.

## Visualization :
Visualize UMAP embeddings, trajectories, and heatmaps for key transitions.



