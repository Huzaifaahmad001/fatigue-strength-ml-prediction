# Machine Learning-Based Prediction of Steel Fatigue Strength

[![Python](https://img.shields.io/badge/Python-3-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-orange.svg)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep_Learning-ff6f00.svg)](https://tensorflow.org/)
[![Jupyter](https://img.shields.io/badge/Environment-Jupyter_Notebook-orange.svg)](https://jupyter.org/)

## Overview

Conventional fatigue testing of structural and automotive steels is time-consuming and resource-intensive. This project applies machine learning to predict rotating-bending fatigue strength at $10^7$ cycles (MPa) directly from chemical composition, heat-treatment parameters, and inclusion metrics across 437 steel samples.

Developed as an undergraduate Final Year Project in Metallurgy and Materials Engineering, this work compares **Random Forest** and **Artificial Neural Network (ANN)** regressors while examining how dataset ordering and steel-family distribution impact model generalization.

---

## Dataset

The repository uses `data.csv`, a preprocessed CSV export of the NIMS MatNavi steel fatigue dataset compiled by Agrawal et al. (2014) (originally distributed as `40192_2013_16_MOESM1_ESM.xlsx`).

| Property | Details |
| :--- | :--- |
| **Total Samples** | 437 (371 carbon & low-alloy, 48 carburizing, 18 spring steels) |
| **Predictors** | 25 continuous features (`Sl. No.` excluded) |
| **Target Variable** | Rotating-bending fatigue strength at $10^7$ cycles (MPa) |
| **Missing Values** | None |

### Feature Breakdown

* **Chemical Composition (9):** `C`, `Si`, `Mn`, `P`, `S`, `Ni`, `Cr`, `Cu`, `Mo`
* **Heat Treatment & Processing (13):** Normalizing temperature; through-hardening temperature, time, and cooling rate; carburization temperature and time; diffusion temperature and time; quenching media temperature; tempering temperature, time, and cooling rate; reduction ratio
* **Inclusion Area Proportions (3):** Deformed inclusions (`dA`), discontinuous array inclusions (`dB`), and isolated inclusions (`dC`)

---

## Methodology & Model Architectures

1. **Preprocessing & Splitting:** Removed the index column (`Sl. No.`) and partitioned the data into an 80/20 train-test split (`random_state=42`). Applied `MinMaxScaler` for neural network training.
2. **Random Forest Regressor:** Ensemble of 100 decision trees (`max_depth=100`, `random_state=42`), evaluated via hold-out metrics, cross-validation, and Gini feature importance.
3. **Artificial Neural Network (ANN):** Sequential dense network (`64 → 32 → 16 → 8 → 1` neurons) with ReLU hidden activations, Adam optimizer, MSE loss, and early stopping on validation loss.
4. **Validation & Stability Testing:** Assessed generalization using shuffled vs. contiguous 5-fold cross-validation and quantified seed sensitivity across five random states.

---

## Results & Key Findings

### Hold-Out Test Performance (80/20 Split)

Both models achieved high accuracy on the random test split, with Random Forest outperforming the ANN in both variance explained and prediction error:

| Model | $R^2$ Score | RMSE (MPa) |
| :--- | :---: | :---: |
| **Random Forest** | **0.985** | **25.196** |
| **Artificial Neural Network (ANN)** | 0.976 | 31.305 |

### Impact of Validation Strategy (Random Forest)

Evaluating Random Forest across different splitting strategies revealed a critical structural property of the NIMS dataset:

| Validation Strategy | $R^2$ Score | RMSE (MPa) |
| :--- | :---: | :---: |
| **Random 80/20 Hold-Out** | 0.985 | 25.196 |
| **Shuffled 5-Fold CV** | 0.977 | 27.295 |
| **Contiguous 5-Fold CV** | -1.586 | 135.979 |

* **Why contiguous CV fails:** The dataset is ordered by steel family, placing all 48 high-strength carburizing steel samples consecutively at the end. In contiguous 5-fold CV, the final fold isolates the entire carburizing steel family into the test set, forcing the model to extrapolate outside its training domain. Random splits mask this domain shift, highlighting the need for steel-family-aware group validation in materials informatics.

### Random Seed Sensitivity (5 Seeds)

| Model | Mean $R^2$ | Mean RMSE (MPa) |
| :--- | :---: | :---: |
| **Random Forest** | $0.985 \pm 0.000$ | $24.662 \pm 0.217$ |
| **Artificial Neural Network** | $0.978 \pm 0.004$ | $29.795 \pm 2.866$ |

Random Forest exhibited near-zero variance across random seeds, whereas ANN convergence introduced higher run-to-run variability.

### Top Predictive Features (Random Forest)

| Rank | Feature | Importance |
| :--- | :--- | :---: |
| 1 | **Tempering Time** | 0.136 |
| 2 | **Carburization Temperature** | 0.113 |
| 3 | **Chromium (`Cr`)** | 0.110 |
| 4 | **Diffusion Temperature** | 0.109 |
| 5 | **Diffusion Time** | 0.097 |

> **Note:** Feature importance reflects predictive utility rather than direct physical causality—carburization and diffusion parameters also act as proxies distinguishing carburized grades from baseline carbon/low-alloy steels.

---

## Limitations & Future Directions

* **Domain Shift & Sample Size:** With 437 samples unevenly distributed across steel classes, random splits overestimate out-of-family generalization. Future iterations should enforce `GroupKFold` validation grouped by steel grade/processing route.
* **Missing Microstructural State:** Composition and bulk thermal schedules omit explicit microstructural descriptors (e.g., prior austenite grain size, retained austenite fraction, hardness profiles). Incorporating physics-informed descriptors or CALPHAD phase predictions could improve extrapolation across alloy families.

---

## Repository Structure

```text
├── Final_Year_Project_fatigue_strength_prediction.ipynb   # Main analysis, training, and evaluation notebook
├── data.csv                                               # Preprocessed NIMS steel fatigue dataset (437 × 27)
└── README.md
```

## Quickstart

1. **Clone the repository and install dependencies:**

   ```bash
   git clone https://github.com/Huzaifaahmad001/REPOSITORY.git
   cd REPOSITORY
   pip install numpy pandas matplotlib scikit-learn tensorflow jupyter
   ```

2. **Configure dataset path and run:**
   * **Google Colab:** Upload `data.csv` to `/content/data.csv` and run all cells.
   * **Local Jupyter:** Update the data-loading line in the notebook from `pd.read_csv('/content/data.csv')` to `pd.read_csv('data.csv')`, then execute top to bottom.

---

## Reference

* Agrawal, A., Deshpande, P. D., Cecen, A., Basavarsu, G. P., Choudhary, A. N., & Kalidindi, S. R. (2014). Exploration of data science techniques to predict fatigue strength of steel from composition and processing parameters. *Integrating Materials and Manufacturing Innovation*, 3(1), 90–108. https://doi.org/10.1186/2193-9772-3-8
* **Supplementary Dataset:** [Preprocessed NIMS MatNavi Data (XLSX)](https://media.springernature.com/original/springer-static/esm/art%3A10.1186%2F2193-9772-3-8/MediaObjects/40192_2013_16_MOESM1_ESM.xlsx)
