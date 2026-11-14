# Machine Learning-Based Prediction of Steel Fatigue Strength

[![Python](https://img.shields.io/badge/Python-3-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine_Learning-orange.svg)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Deep_Learning-ff6f00.svg)](https://tensorflow.org/)
[![Jupyter](https://img.shields.io/badge/Environment-Jupyter_Notebook-orange.svg)](https://jupyter.org/)

## Overview

This project explores the application of machine learning to predict the fatigue strength of steels using chemical composition and manufacturing parameters.

Using a dataset of 437 steel samples, I developed and compared two regression models: Random Forest and Artificial Neural Network (ANN). The objective was to investigate how alloy composition, heat treatment conditions, and processing parameters influence the prediction of fatigue strength at 10⁷ cycles.

The project combines materials engineering knowledge with data analysis and machine learning to explore composition–processing–property relationships in metallic materials.

*Developed as my undergraduate Final Year Project in Metallurgy and Materials Engineering.*

## Problem Statement

Fatigue failure is a major concern in structural and automotive components. Conventional fatigue testing requires considerable experimental time and resources.

This project investigates whether machine learning can predict fatigue strength from material composition and processing history, potentially supporting more efficient materials evaluation.

**Prediction target:** Rotating-bending fatigue strength at 10⁷ cycles (MPa).

## Dataset and Source

The project uses `data.csv`, a CSV-format version of the preprocessed NIMS MatNavi steel fatigue dataset provided as supplementary material in:

**Agrawal et al. (2014)** – *Exploration of data science techniques to predict fatigue strength of steel from composition and processing parameters.*

The original supplementary workbook is named `40192_2013_16_MOESM1_ESM.xlsx` and is titled *Preprocessed NIMS MatNavi Data used in this study*.

**Dataset characteristics:**

| Characteristic | Details |
|---|---|
| Total samples | 437 |
| Input features | 25 |
| Target variable | Fatigue strength |
| Units | MPa |
| Missing values | None |
| Steel categories | Carbon, low-alloy, carburizing and spring steels |

The original study reports the following sample distribution:

- 371 carbon and low-alloy steel samples
- 48 carburizing steel samples
- 18 spring steel samples

### Input Features

The 25 input features cover:

**1. Chemical Composition**
- C, Si, Mn, P, S, Ni, Cr, Cu and Mo.

**2. Heat Treatment and Processing Parameters**
- Normalizing temperature
- Through-hardening temperature, time and cooling rate
- Carburization temperature and time
- Diffusion temperature and time
- Quenching media temperature
- Tempering temperature, time and cooling rate

**3. Other Material Parameters**
- Reduction ratio
- Inclusion area proportions (dA, dB and dC)

The serial number column is excluded from model training.

## Methodology

The project follows a machine learning regression workflow:

1. **Data inspection:** Examined dataset structure, feature types and missing values.
2. **Exploratory data analysis:** Investigated feature distributions and correlations with fatigue strength.
3. **Data splitting:** Divided the dataset into 80% training and 20% testing using a fixed random seed (42).
4. **Model development:** Trained Random Forest and Artificial Neural Network regression models.
5. **Performance evaluation:** Compared predictions using R² and Root Mean Squared Error (RMSE).
6. **Validation analysis:** Investigated five-fold cross-validation strategies and model sensitivity to random seeds.

### Models Implemented

**1. Random Forest Regressor**

- 100 decision trees
- Maximum tree depth: 100
- Random state: 42
- Feature importance analysis

**2. Artificial Neural Network (ANN)**

- Four hidden layers
- Architecture: 64 → 32 → 16 → 8 → 1 neurons
- ReLU activation in hidden layers
- Adam optimizer
- Mean squared error loss
- Min-Max feature and target scaling
- Early stopping to monitor validation performance

## Results

### Model Performance

Both models demonstrated strong predictive performance on the random 80/20 test split.

| Model | R² Score | RMSE (MPa) |
|---|---:|---:|
| Random Forest | **0.985** | **25.196** |
| Artificial Neural Network | 0.976 | 31.305 |

The Random Forest model achieved better performance on the selected test split, with a higher R² score and lower prediction error.

### Cross-Validation Analysis

Random Forest was additionally evaluated using two five-fold cross-validation strategies.

| Evaluation Strategy | R² Score | RMSE (MPa) |
|---|---:|---:|
| Random 80/20 hold-out | 0.985 | 25.196 |
| Shuffled 5-fold CV | 0.977 | 27.295 |
| Contiguous 5-fold CV | -1.586 | 135.979 |

The significant difference between shuffled and contiguous cross-validation highlights the importance of dataset structure during model evaluation.

The dataset is ordered, with all 48 carburizing steel samples appearing consecutively at the end. These samples also have substantially higher average fatigue strength than the other samples.

Consequently, the final contiguous validation fold contains all 48 carburized samples, making prediction considerably more difficult.

This demonstrates why random splitting can produce optimistic estimates when predicting across different steel families. Group-based validation should be investigated in future work.

### Random Seed Sensitivity

The models were also evaluated using five different random seeds to examine the consistency of their predictions.

| Model | Mean R² | Mean RMSE (MPa) |
|---|---:|---:|
| Random Forest | 0.985 ± 0.000 | 24.662 ± 0.217 |
| Neural Network | 0.978 ± 0.004 | 29.795 ± 2.866 |

Random Forest demonstrated more consistent performance across the tested seeds, while the ANN exhibited greater variation.

## Feature Importance

Random Forest feature importance was used to identify the input variables contributing most to model predictions.

The five highest-ranked features were:

| Feature | Importance |
|---|---:|
| Tempering Time | 0.136 |
| Carburization Temperature | 0.113 |
| Chromium (Cr) | 0.110 |
| Diffusion Temperature | 0.109 |
| Diffusion Time | 0.097 |

The results highlight the predictive contribution of both heat treatment conditions and chemical composition.

However, feature importance indicates predictive contribution rather than direct causality. Some processing parameters also distinguish different steel categories within the dataset.

## Visualizations

The notebook includes:

- Histograms of processing parameters.
- Correlation analysis between input features and fatigue strength.
- Random Forest feature importance.
- ANN training and validation loss curves.

## Limitations and Future Work

**Limitations**

- Relatively small dataset of 437 samples.
- Differences in sample distribution between steel categories.
- Random train-test splitting may overestimate generalization performance.
- Explicit microstructural descriptors, such as grain size and phase fractions, are not included.
- Feature importance does not establish causal relationships.

**Future Work**

- Expand the dataset with additional experimental measurements.
- Introduce steel-family-aware and grouped validation strategies.
- Incorporate microstructural descriptors into prediction models.
- Explore physics-informed machine learning approaches.
- Integrate computational materials modeling and atomistic simulations.

## Tools and Technologies

| Category | Tools |
|---|---|
| Programming | Python |
| Data Analysis | Pandas, NumPy |
| Machine Learning | Scikit-Learn |
| Deep Learning | TensorFlow / Keras |
| Visualization | Matplotlib |
| Development Environment | Jupyter Notebook |

## How to Run

Clone the repository:

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
cd REPOSITORY
```

Install the required libraries:

```bash
pip install numpy pandas matplotlib scikit-learn tensorflow jupyter
```

Place `data.csv` in the appropriate directory.

The notebook currently uses the Google Colab path:

```python
df_1 = pd.read_csv('/content/data.csv')
```

For local execution, use:

```python
df_1 = pd.read_csv('data.csv')
```

Open `Final_Year_Project_fatigue_strength_prediction.ipynb` and run all cells.

## Repository Structure

```text
├── Final_Year_Project_fatigue_strength_prediction.ipynb
├── README.md
└── data.csv
```

## References

Agrawal, A., Deshpande, P. D., Cecen, A., Basavarsu, G. P., Choudhary, A. N., & Kalidindi, S. R. (2014).

*Exploration of data science techniques to predict fatigue strength of steel from composition and processing parameters.*

Integrating Materials and Manufacturing Innovation, 3, 90–108.

https://doi.org/10.1186/2193-9772-3-8

**Original supplementary dataset:** [Download Additional File 1 – Preprocessed NIMS MatNavi Data (XLSX)](https://media.springernature.com/original/springer-static/esm/art%3A10.1186%2F2193-9772-3-8/MediaObjects/40192_2013_16_MOESM1_ESM.xlsx)
