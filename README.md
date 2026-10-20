# Data-Driven Fatigue Strength Prediction of Heat-Treated AISI 4140 Steel

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-orange.svg)](https://scikit-learn.org/)
[![TensorFlow](https://img.shields.io/badge/Library-TensorFlow-ff6f00.svg)](https://tensorflow.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🔬 Overview
This project investigates the prediction of fatigue strength in heat-treated AISI 4140 steel using machine learning models trained on compositional and processing parameters. The study demonstrates how data-driven approaches can complement traditional experimental methods to understand structure–property relationships in metallic materials.

*Developed as part of an undergraduate thesis in Metallurgy and Materials Engineering.*

---

## ⚠️ Problem Statement
Fatigue failure is a critical limitation in structural and automotive components. Conventional fatigue testing is time-consuming, expensive, and restricts exploration of large material design spaces. 

This project aims to predict fatigue strength based on:
* Alloy chemical composition
* Heat treatment conditions

---

## 📊 Dataset and Preprocessing
The dataset comprises experimentally measured fatigue strength values along with:
* Alloy composition (C, Cr, Mo, etc.)
* Heat treatment parameters

**Preprocessing steps include:**
* Handling missing values
* Feature scaling and normalization
* Correlation analysis
* Feature selection

---

## ⚙️ Methodology

### Models Implemented
* **Random Forest Regressor**
* **Artificial Neural Network (ANN)**

### Workflow
1. Data preprocessing
2. Exploratory data analysis
3. Feature engineering
4. Model training
5. Performance evaluation using the $R^2$ metric

---

## 📈 Model Performance

| Model | $R^2$ Score |
| :--- | :--- |
| **Random Forest** | **0.986** |
| **ANN** | **0.971** |

The Random Forest model achieved superior performance, effectively capturing nonlinear relationships between input features and fatigue strength.

---

## 📉 Visual Analysis
Key plots included in the repository:
* **Correlation heatmap:** Illustrates relationships between composition, processing parameters, and fatigue strength.
* **Predicted vs Actual values:** Evaluates model accuracy and generalization.
* **Feature importance (Random Forest):** Identifies critical contributors to fatigue strength.

---

## 💡 Key Scientific Insights
* **Alloy Composition Impact:** Strongly influences fatigue strength, particularly C, Cr, and Mo, due to effects on hardenability and microstructure evolution.
* **Heat Treatment Effects:** Significantly affect fatigue performance through phase transformations and grain refinement.
* **Nonlinear Interactions:** The model successfully captures complex interactions between composition and processing that are difficult to isolate experimentally.

---

## 🚧 Limitations & Future Work
* **Limitations:** Limited dataset size may affect generalization; purely data-driven approach without explicit incorporation of physical laws; microstructural descriptors (grain size, phases) are not included.
* **Future Work:** Integrate physics-informed machine learning approaches, include microstructural features, expand datasets, and couple with computational materials modeling (DFT, atomistic simulations).

---

## 🛠️ Tools and Technologies
* **Languages & Core:** Python, Pandas, NumPy
* **Machine Learning:** Scikit-learn, TensorFlow
* **Visualization:** Matplotlib, Seaborn
* **Environment:** Jupyter Notebook

---

## 📁 Repository Structure
```text
├── fatigue_prediction_model.ipynb
├── README.md
├── requirements.txt
├── data.csv
└── plots/
    ├── correlation_heatmap.png
    ├── predicted_vs_actual.png
    └── feature_importance.png
