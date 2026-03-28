# Data-Driven Fatigue Strength Prediction of Heat-Treated AISI 4140 Steel

## Overview
This project investigates the prediction of fatigue strength in heat-treated AISI 4140 steel using machine learning models trained on compositional and processing parameters. The study demonstrates how data-driven approaches can complement traditional experimental methods to understand structure–property relationships in metallic materials.

Developed as part of an undergraduate thesis in Metallurgy and Materials Engineering.

## Problem Statement
Fatigue failure is a critical limitation in structural and automotive components. Conventional fatigue testing is time-consuming, expensive, and restricts exploration of large material design spaces.

This project aims to predict fatigue strength based on:

- Alloy chemical composition
- Heat treatment conditions

## Dataset and Preprocessing
The dataset comprises experimentally measured fatigue strength values along with:

- Alloy composition (C, Cr, Mo, etc.)
- Heat treatment parameters

Preprocessing steps include:

- Handling missing values
- Feature scaling and normalization
- Correlation analysis
- Feature selection

## Methodology
### Models Implemented
- Random Forest Regressor
- Artificial Neural Network (ANN)

### Workflow
1. Data preprocessing  
2. Exploratory data analysis  
3. Feature engineering  
4. Model training  
5. Performance evaluation using the R² metric

## Model Performance

| Model          | R² Score |
|----------------|----------|
| Random Forest  | 0.986    |
| ANN            | 0.971    |

The Random Forest model achieved superior performance, effectively capturing nonlinear relationships between input features and fatigue strength.

## Visual Analysis
Key plots included in the notebook:

- **Correlation heatmap**: illustrates relationships between composition, processing parameters, and fatigue strength  
- **Predicted vs Actual values**: evaluates model accuracy and generalization  
- **Feature importance (Random Forest)**: identifies critical contributors to fatigue strength  

Plots are embedded in the notebook and can be exported as PNG for clarity.

## Key Scientific Insights
- Alloy composition strongly influences fatigue strength, particularly C, Cr, and Mo, due to effects on hardenability and microstructure evolution.  
- Heat treatment conditions significantly affect fatigue performance through phase transformations and grain refinement.  
- The model captures nonlinear interactions between composition and processing that are difficult to isolate experimentally.

## Limitations
- Limited dataset size may affect generalization  
- Purely data-driven approach without explicit incorporation of physical laws  
- Microstructural descriptors (grain size, phases) are not included

## Future Work
- Integrate physics-informed machine learning approaches  
- Include microstructural features  
- Expand to larger and more diverse datasets  
- Couple with computational materials modeling (DFT, atomistic simulations)

## Tools and Technologies
- Python, Pandas, NumPy  
- Scikit-learn, TensorFlow  
- Matplotlib, Seaborn  
- Jupyter Notebook

## Repository Structure
Final_Year_Project_fatigue_strength_prediction.ipynb
README.md
plots/
    correlation_heatmap.png
    predicted_vs_actual.png
    feature_importance.png
requirements.txt

## Relevance to Computational Materials Science

This project aligns with current trends in computational materials science, where machine learning and data-driven approaches are increasingly used to predict material properties, accelerate alloy design, and complement physics-based modeling. The methodology demonstrates how AI can uncover complex structure–property relationships, providing insights that are difficult to obtain solely through experimental testing. Such approaches are widely applicable in fields like fatigue analysis, electrochemical materials, and energy storage systems.


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
