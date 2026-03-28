# Data-Driven Fatigue Strength Prediction of Heat-Treated 4140 Steel

## 📌 Overview
This project predicts fatigue strength in heat-treated AISI 4140 alloy steel using machine learning models trained on compositional and processing parameters. It demonstrates how data-driven approaches complement traditional experimental methods in understanding structure–property relationships in metallic materials.

Developed as part of an undergraduate thesis in Metallurgy and Materials Engineering.

---

## 🎯 Problem Statement
Fatigue failure is a critical limitation in structural and automotive components. Conventional fatigue testing is time-consuming, expensive, and limits exploration of large material design spaces.

This project predicts fatigue strength based on:
- Chemical composition  
- Heat treatment conditions

---

## 📊 Dataset & Preprocessing
The dataset consists of experimentally measured fatigue strength values along with:
- Alloy composition (C, Cr, Mo, etc.)  
- Heat treatment parameters  

**Preprocessing steps:**
- Handling missing values  
- Feature scaling and normalization  
- Correlation analysis  
- Feature selection  

---

## 🧠 Methodology
**Models Implemented:**
- Random Forest Regressor  
- Artificial Neural Network (ANN)  

**Workflow:**
- Data preprocessing  
- Exploratory data analysis  
- Feature engineering  
- Model training  
- Performance evaluation (R² metric)  

---

## 📈 Model Performance

| Model | R² Score |
|-------|----------|
| Random Forest | 0.986 |
| ANN | 0.971 |

Random Forest achieved superior performance, capturing nonlinear relationships between input features and fatigue strength.

---

## 📊 Visual Analysis
**Included plots:**
- Correlation heatmap — reveals relationships between composition, processing parameters, and fatigue strength  
- Predicted vs Actual values — shows model accuracy and generalization  
- Feature importance (Random Forest) — identifies key contributors to fatigue strength  

*(Plots are embedded in the notebook and can be exported as PNG for clarity)*

---

## 🔬 Key Scientific Insights
- Alloy composition strongly influences fatigue strength, particularly C, Cr, and Mo, due to effects on hardenability and microstructure evolution.  
- Heat treatment conditions significantly affect fatigue performance through phase transformations and grain refinement.  
- The model captures nonlinear interactions between composition and processing that are difficult to isolate experimentally.  

---

## ⚠️ Limitations
- Limited dataset size may affect model generalization  
- Approach is purely data-driven, without explicit incorporation of physical laws  
- Microstructural descriptors (grain size, phases) are not included  

---

## 🚀 Future Work
- Integrate physics-informed machine learning approaches  
- Include microstructural features  
- Expand to larger and more diverse datasets  
- Couple with computational materials modeling (DFT, atomistic simulations)  

---

## 🛠️ Tools & Technologies
- Python, Pandas, NumPy  
- Scikit-learn, TensorFlow  
- Matplotlib, Seaborn  
- Jupyter Notebook  

---

## 📁 Repository Structure

├── Final_Year_Project_fatigue_strength_prediction.ipynb
├── README.md
└── (optional) plots/
├── correlation_heatmap.png
├── predicted_vs_actual.png
└── feature_importance.png


---

## ▶️ How to Run
1. Clone the repository  
2. Install required Python libraries  
3. Open the notebook and run all cells sequentially  

---

## 👤 Author
**Huzaifa Ahmad**  
Materials Engineer | Electrochemistry & Data-Driven Materials Modeling  
📧 huzaifaahmad805@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/huzaifa-ahmad24)  

---

## 📌 Note
This project reflects ongoing work toward integrating data-driven methods with materials science to improve prediction and understanding of material performance in engineering applications.
