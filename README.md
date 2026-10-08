# Single-cell foundation models in colorectal cancer

This repository contains the computational pipeline and standalone Jupyter Notebooks for cross-architecture single-cell foundation model screening to identify cryptic targets and metabolic vulnerabilities in metastatic colorectal cancer (mCRC).

## Overview

Adaptive resistance to cytotoxic frontline chemotherapy (such as FOLFIRI) is a critical challenge in clinical oncology. While static genomic screens often fail to capture dynamic cell-state transitions, single-cell foundation models leverage transformer architectures pre-trained on millions of single-cell transcriptomes to simulate *in silico* perturbations. 

This pipeline deploys two independent deep learning architectures—**scGPT** and **Geneformer**—to execute parallel virtual knockout screening on post-treatment clinical single-cell transcriptomic datasets. 

## Key Features

* **Metacell Aggregation:** High-fidelity micro-clustering using KNN graphs and Louvain modularity to minimize technical dropouts and handle transformer context limits.
* **Cross-Architecture Integration:** Execution of *in silico* CRISPR knockouts across different embedding mechanisms:
  * **scGPT Pipeline:** Vector-space analysis using continuous log-normalized expression.
  * **Geneformer Pipeline:** Sequence-based analysis via Rank-Value Tokenization.
* **Consensus Trajectory Mapping:** Evaluation of phenotypic shifts based on directional trajectories pointing from non-responder (chemoresistant) to responder (chemosensitive) cell-count-weighted clinical centroids.
* **Robust Convergence:** Extraction of a robust consensus target signature (`CD44`, `SGK1`, `CAMKK2`, `IRAK2`, `KDELR2`).
## Prerequisites & Installation

The implementation bypasses native `torchtext` dependencies, securing full runtime stability on modern Python environments. 

Ensure you have the required foundation weights (`best_model.pt` for scGPT and `Geneformer-V2-316M` for Geneformer) downloaded into your local storage paths before running the scripts.

```bash
pip install numpy pandas scanpy scikit-learn networkx torch transformers python-louvain
```
