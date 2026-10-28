# Raman Spectra Analysis for Healthcare Applications

This repository contains a set of Jupyter notebooks for Raman spectroscopy analysis in two main experimental directions:

- bacterial species classification using deep learning models
- urine spectral preprocessing and transfer-learning experiments

## Requirements

Install the project dependencies with:

```bash
pip install -r requirements.txt
```

Key dependencies include:

- TensorFlow / Keras
- RamanSPy
- NumPy and Pandas
- Matplotlib and Seaborn
- Scikit-learn

## Repository overview

### Bacteria workflow

The [Bacteria](Bacteria) folder contains the main deep-learning experiments for bacterial Raman spectra classification.

Relevant notebooks:

- [Bacteria/plot_bacteria.ipynb](Bacteria/plot_bacteria.ipynb): exploratory spectral visualization and class inspection
- [Bacteria/ramannet_crossv.ipynb](Bacteria/ramannet_crossv.ipynb): earlier RamanNet-style cross-validation baseline
- [Bacteria/improved_ramannet.ipynb](Bacteria/improved_ramannet.ipynb): main model training and fine-tuning workflow

Additional folders:

- [Bacteria/data](Bacteria/data): dataset directory for the main bacterial Raman data
- [Bacteria/ramannet_folds](Bacteria/ramannet_folds): saved fold-specific trained models
- [Bacteria/runs](Bacteria/runs): experiment outputs, checkpoints, figures, and candidate weights
- [Bacteria/poster_assets](Bacteria/poster_assets): figures and assets for presentations

### Urine workflow

The [Urine](Urine) folder contains an exploratory urine-analysis pipeline for preprocessing and transfer-learning experiments.

Relevant notebooks:

- [Urine/prepare_dataset.ipynb](Urine/prepare_dataset.ipynb): prepares raw urine CSV spectra into processed arrays
- [Urine/urine spectrum preprocessing tests.ipynb](Urine/urine spectrum preprocessing tests.ipynb): preprocessing and quality-control experiments
- [Urine/transfer learning ramannet.ipynb](Urine/transfer learning ramannet.ipynb): transfer-learning prototype for RamanNet-based modeling

Additional folders:

- [Urine/dataset](Urine/dataset): processed urine datasets
- [Urine/saudaveis](Urine/saudaveis): healthy urine spectra
- [Urine/doentes](Urine/doentes): diseased urine spectra

## Data availability

### Included in the repository

The following data are already present:

- processed urine datasets in [Urine/dataset](Urine/dataset)
- raw urine CSV files in [Urine/saudaveis](Urine/saudaveis) and [Urine/doentes](Urine/doentes)
- experiment outputs and saved model artifacts under [Bacteria/runs](Bacteria/runs)

### Download required

The main bacterial dataset is not stored directly in this repository and must be downloaded externally.

1. Download the dataset folder from:
   https://www.dropbox.com/sh/gmgduvzyl5tken6/AABtSWXWPjoUBkKyC2e7Ag6Da?dl=0
2. Place the downloaded `data` folder inside the [Bacteria](Bacteria) directory
3. Ensure the expected files are present, such as `X_reference.npy`, `y_reference.npy`, `X_finetune.npy`, `y_finetune.npy`, and `X_test.npy`

> Note: the urine data are already included in the repository, whereas the bacterial dataset requires an external download.

## Repository structure

```text
.
├── .gitignore
├── README.md
├── requirements.txt
├── references/
│   ├── contrastive_learning/
│   │   ├── README.md
│   │   ├── 1-s2.0-S0169743925000693-main.pdf
│   │   └── 1-s2.0-S0169743925000693-supporting info.pdf
│   └── Ramannet/
│       ├── README.md
│       └── ramannet.pdf
├── Bacteria/
│   ├── data/                      # external bacterial dataset (download required)
│   ├── improved_ramannet.ipynb
│   ├── plot_bacteria.ipynb
│   ├── poster_assets/
│   ├── ramannet_crossv.ipynb
│   ├── ramannet_folds/
│   └── runs/
│       └── <experiment_name>/
│           ├── checkpoints/
│           ├── figures/
│           └── models/
├── Urine/
│   ├── .ipynb_checkpoints/
│   ├── dataset/
│   ├── doentes/
│   ├── prepare_dataset.ipynb
│   ├── saudaveis/
│   ├── transfer learning ramannet.ipynb
│   └── urine spectrum preprocessing tests.ipynb
├── tmp/
│   └── pdfs/
└── LICENSE (to be added if needed)
```

## Important notes

- The [Bacteria](Bacteria) workflow is the primary experimental pipeline in this repository, and [Bacteria/improved_ramannet.ipynb](Bacteria/improved_ramannet.ipynb) is the main work to continue developing further.
- The improved RamanNet workflow achieved an accuracy of 84.77%, outperforming the earlier cross-validation notebook, which achieved 83.43%.
- The [Urine](Urine) workflow is exploratory and should be interpreted as a research prototype.
- Some saved model files under [Bacteria/runs](Bacteria/runs) and [Bacteria/ramannet_folds](Bacteria/ramannet_folds) may be experimental or unverified; they should be used with caution.
- Notebook outputs may contain local file paths or run-specific metadata that are not part of the repository structure itself.

## Future work: contrastive learning

### Benchmark objective

The original RamanNet paper reported an accuracy of approximately 85% for Raman-based classification. The article PDF is stored in [references/Ramannet](references/Ramannet):

Ibtehaz, N., Chowdhury, M. E. H., Khandakar, A., _et al._ (2023). RamanNet: A generalized neural network architecture for Raman spectrum analysis. _Neural Computing and Applications, 35_, 18719–18735. https://doi.org/10.1007/s00521-023-08700-z

The main objective is to explore different deep-learning model architectures and exceed this reported benchmark on the bacterial classification task. Contrastive learning is one possible future approach, informed by the article below:

Shi, Z., Wang, J., Su, Y., Liang, X., Zi, J., Wang, C., Bi, H., & Xiang, X. (2025). _Transfer contrastive learning for Raman spectra data of urine: Detection of glucose, protein, and prediction of kidney disorders_. **Chemometrics and Intelligent Laboratory Systems, 261**, 105384. https://doi.org/10.1016/j.chemolab.2025.105384

The article PDF and the authors' supporting information are stored in [references/contrastive_learning](references/contrastive_learning).

## Review-only usage and funding acknowledgement

This repository is made available for academic review, evaluation, and expert feedback. The code and materials are provided for research and inspection purposes only and are not intended for reuse, modification, redistribution, or commercial use without explicit written permission from the author.

Project: Deep Learning Methods for Output Extraction in Photonic Biosensors for Healthcare Applications (project link: https://doi.org/10.54499/2022.13579.BD)

This work was supported by Portuguese national funds through the Fundação para a Ciência e a Tecnologia (FCT), under the grant 2022.13579.BD.

Any reference to this repository or the associated work should acknowledge the project and the FCT funding support.
