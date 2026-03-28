# Data-Driven Fatigue Strength Prediction of Heat-Treated 4140 Steel

## 📌 Overview
This project investigates the prediction of fatigue strength in heat-treated AISI 4140 alloy steel using machine learning models trained on compositional and processing parameters. The work demonstrates how data-driven approaches can complement traditional experimental methods in understanding structure–property relationships in metallic materials.

Developed as part of an undergraduate thesis in Metallurgy and Materials Engineering.

---

## 🎯 Problem Statement
Fatigue failure is a critical limitation in structural and automotive components. Conventional fatigue testing is time-consuming, expensive, and limits exploration of large material design spaces.

This project addresses the problem by developing machine learning models to predict fatigue strength based on:
- Chemical composition
- Heat treatment conditions

---

## 📊 Dataset & Preprocessing
The dataset consists of experimentally measured fatigue strength values along with:

- Alloy composition (C, Cr, Mo, etc.)
- Heat treatment parameters

### Preprocessing steps:
- Missing value handling  
- Feature scaling and normalization  
- Correlation analysis  
- Feature selection  

---

## 🧠 Methodology

Two supervised learning models were implemented:

- **Random Forest Regressor**
- **Artificial Neural Network (ANN)**

### Workflow:
1. Data preprocessing  
2. Exploratory data analysis  
3. Feature engineering  
4. Model training  
5. Performance evaluation (R² metric)  

---

## 📈 Model Performance

| Model | R² Score |
|------|--------|
| Random Forest | 0.986 |
| ANN | 0.971 |

The Random Forest model achieved superior predictive performance, indicating strong capability in capturing nonlinear relationships between input features and fatigue strength.

---

## 📊 Visual Analysis

### 🔹 Correlation Heatmap
- Reveals relationships between composition, processing parameters, and fatigue strength  
- Highlights dominant influencing variables  

### 🔹 Predicted vs Actual Values
- Demonstrates strong agreement between predicted and experimental fatigue strength  
- Indicates high model accuracy and generalization  

### 🔹 Feature Importance (Random Forest)
- Identifies key contributors to fatigue strength  
- Confirms the influence of alloying elements and heat treatment parameters  

*(All plots are available in the Jupyter Notebook)*

---

## 🔬 Key Scientific Insights

- **Alloy composition strongly influences fatigue strength**, particularly carbon and alloying elements such as chromium and molybdenum, due to their role in hardenability and microstructural evolution.  

- **Heat treatment conditions significantly affect fatigue performance**, likely through phase transformations and grain refinement mechanisms.  

- The model captures **nonlinear interactions between composition and processing**, which are difficult to isolate using traditional experimental approaches alone.  

- Results demonstrate that **machine learning can approximate complex structure–property relationships** in metallic systems.

---

## ⚠️ Limitations

- Dataset size is limited, which may restrict model generalization  
- The approach is purely data-driven and does not explicitly incorporate physical laws  
- Microstructural descriptors (grain size, phases) are not directly included  

---

## 🚀 Future Work

- Integration of **physics-informed machine learning approaches**  
- Inclusion of **microstructural features**  
- Expansion to larger datasets  
- Coupling with **computational materials science methods (e.g., DFT, atomistic modeling)**  

---

## 🛠️ Tools & Technologies
- Python  
- Pandas, NumPy  
- Scikit-learn  
- TensorFlow  
- Matplotlib, Seaborn  
- Jupyter Notebook  

---

## 📁 Repository Structure


---

## ▶️ How to Run
1. Clone the repository  
2. Install required Python libraries  
3. Open the notebook  
4. Run all cells sequentially  

---

## 👤 Author
**Huzaifa Ahmad**  
Materials Engineer | Electrochemistry & Data-Driven Materials Modeling  
📧 huzaifaahmad805@gmail.com  
🔗 https://linkedin.com/in/huzaifa-ahmad24  

---

## 📌 Note
This project reflects ongoing work toward integrating data-driven methods with materials science to improve prediction and understanding of material performance in engineering applications.
