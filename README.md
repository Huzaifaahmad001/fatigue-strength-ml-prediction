# Data-Driven Fatigue Strength Prediction of Heat-Treated 4140 Steel

## 📌 Overview
This project applies machine learning to predict the fatigue strength of heat-treated AISI 4140 alloy steel using compositional and processing parameters. The goal is to demonstrate how data-driven approaches can complement traditional experimental methods in evaluating material performance.

This work was conducted as part of my undergraduate thesis in Metallurgy and Materials Engineering.

---

## 🎯 Problem Statement
Fatigue failure is a critical limitation in structural and automotive components. Conventional fatigue testing is time-intensive, costly, and often impractical for exploring large design spaces.

This project investigates whether machine learning models can accurately predict fatigue strength based on:
- Chemical composition
- Heat treatment conditions

---

## 📊 Dataset & Preprocessing
The dataset consists of experimentally measured fatigue strength values along with:
- Alloy composition (C, Cr, Mo, etc.)
- Heat treatment parameters

### Preprocessing steps:
- Handling missing values
- Feature scaling and normalization
- Correlation analysis
- Feature selection

---

## 🧠 Methodology
Two supervised learning models were implemented:

- **Random Forest Regressor**
- **Artificial Neural Network (ANN)**

The workflow includes:
1. Data cleaning and preprocessing  
2. Feature engineering  
3. Model training and validation  
4. Performance evaluation using R² score  

---

## 📈 Model Performance

| Model | R² Score |
|------|--------|
| Random Forest | 0.986 |
| ANN | 0.971 |

The Random Forest model demonstrated superior performance and robustness for this dataset.

---

## 🔬 Key Scientific Insights

- **Alloy composition plays a dominant role** in fatigue strength, particularly carbon and alloying elements (e.g., Cr, Mo), due to their influence on hardenability and microstructure evolution.  
- **Heat treatment conditions significantly affect fatigue resistance**, likely through phase transformations and microstructural refinement.  
- The model captured **nonlinear interactions between composition and processing**, highlighting the complexity of fatigue behavior in alloy steels.  
- Results indicate that **machine learning can effectively approximate structure–property relationships** in metallic systems.

---

## 📊 Visual Analysis
*(Add plots here in your repo)*  
- Feature importance (Random Forest)  
- Correlation heatmap  
- Predicted vs actual fatigue strength  

---

## ⚠️ Limitations

- Dataset size is limited, which may affect model generalization  
- The approach is purely data-driven and does not explicitly incorporate physical laws  
- Microstructural descriptors are not directly included  

---

## 🚀 Future Work

- Integration of **physics-informed machine learning**  
- Inclusion of **microstructural features** (grain size, phases)  
- Expansion to **larger and more diverse datasets**  
- Coupling with **computational materials modeling approaches**  

---

## 🛠️ Tools & Technologies
- Python  
- Pandas, NumPy  
- Scikit-learn  
- TensorFlow  
- Jupyter Notebook  

---

## 📁 Repository Structure

---

## ▶️ How to Run
1. Clone the repository  
2. Install required Python libraries  
3. Open the notebook and run all cells  

---

## 👤 Author
**Huzaifa Ahmad**  
Materials Engineer | Electrochemistry & Data-Driven Materials Modeling  
📧 huzaifaahmad805@gmail.com  
🔗 https://linkedin.com/in/huzaifa-ahmad24  

---

## 📌 Note
This project demonstrates the application of machine learning to materials science problems and reflects ongoing interest in combining data-driven and physical approaches for materials design and performance prediction.
