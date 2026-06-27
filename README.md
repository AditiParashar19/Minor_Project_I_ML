# Minor_Project_1

<div align="center">

# 🌾 Crop Recommendation System
### *Smart Agriculture Powered by Machine Learning*

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)](https://scikit-learn.org)
[![Pandas](https://img.shields.io/badge/Pandas-Data-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)]()

<br/>

> **An intelligent ML-based system that recommends the most suitable crop based on soil nutrients and climatic conditions — helping farmers make data-driven agricultural decisions.**

<br/>

![Crop Recommendation Banner](https://img.shields.io/badge/🌱_Precision_Agriculture-Machine_Learning_Project-2E8B57?style=flat-square&labelColor=1a5c35)

</div>

---

## 📑 Table of Contents

- [ Problem Statement](#-problem-statement)
- [ Project Objectives](#-project-objectives)
- [ Dataset](#-dataset)
- [ Methodology](#️-methodology)
- [ Exploratory Data Analysis](#-exploratory-data-analysis)
- [ Model Development](#-model-development)
- [ Results & Evaluation](#-results--evaluation)
- [ Conclusion](#-conclusion)
- [ Tech Stack](#️-tech-stack)
- [ Project Structure](#-project-structure)
- [ How to Run](#-how-to-run)
- [ References](#-references)

---

##  Problem Statement

Agriculture plays a vital role in the economy, and selecting the **right crop** is essential for high productivity. Farmers often face challenges in choosing the most suitable crop due to variations in:

-  Soil nutrient levels
-  Temperature and humidity
-  Rainfall patterns
-  Soil pH values

> **Incorrect crop selection leads to poor yields, resource inefficiency, and financial losses.**

This project develops a **Crop Recommendation System** using supervised machine learning that accurately predicts the most suitable crop by analyzing soil and environmental parameters.

---

##  Project Objectives

| # | Objective |
|---|-----------|
| 1 | Analyze agricultural data from reliable sources |
| 2 | Preprocess the dataset for ML applications |
| 3 | Perform Exploratory Data Analysis (EDA) |
| 4 | Build supervised ML models (KNN, Logistic Regression, Random Forest) |
| 5 | Determine optimal hyperparameters for highest accuracy |
| 6 | Evaluate models using Accuracy, Precision, Recall, and F1-Score |
| 7 | Assist farmers in making informed, data-driven crop decisions |

---

##  Dataset

<div align="center">

[![Kaggle](https://img.shields.io/badge/Source-Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset)

</div>

**Dataset:** Crop Recommendation Dataset by Atharva Ingle

| Property | Value |
|----------|-------|
|  Total Records | 2,200 |
|  Features | 8 (7 input + 1 target) |
| 🌾 Crop Classes | 22 unique crops |
|  Class Balance | Perfectly balanced (100 samples/class) |
| ❌ Missing Values | None |
|  Duplicates | None |

### Input Features

| Feature | Description | Unit |
|---------|-------------|------|
| **N** | Nitrogen content in soil | Ratio |
| **P** | Phosphorus content in soil | Ratio |
| **K** | Potassium content in soil | Ratio |
| **Temperature** | Ambient temperature | °C |
| **Humidity** | Relative humidity | % |
| **pH** | Soil pH value | — |
| **Rainfall** | Rainfall measurement | mm |

###  Target Variable

**Label** — 22 Crop Classes:

```
🌾 Rice       🌽 Maize        🫘 Chickpea      🫘 Kidneybeans   🫘 Pigeonpeas
🫘 Mothbeans  🫘 Mungbean     🫘 Blackgram     🫘 Lentil        🍎 Apple
🍌 Banana     🥭 Mango        🍇 Grapes        🍉 Watermelon    🍈 Muskmelon
🍊 Orange     🍈 Papaya       🥥 Coconut       🌸 Pomegranate   🌿 Cotton
🌿 Jute       ☕ Coffee
```

---

## ⚙️ Methodology

```
ML Pipeline

Data Loading -> Pre Processing -> EDA Analysis -> Feature Selection -> Train-Test Split -> Model Training (KNN,Random Forest,Logistic Regression) -> Prediction -> Model Evaluation 

```

###  Data Preprocessing Steps

<details>
<summary><b>Click to expand preprocessing details</b></summary>

1. **Data Loading** — Imported using Pandas; inspected with `head()`, `info()`, `describe()`
2. **Missing Value Check** — `isnull().sum()` → ✅ No missing values found
3. **Duplicate Removal** — `duplicated()` → ✅ No duplicates found
4. **Label Encoding** — Target variable (crop names) encoded into numerical classes
5. **Feature Scaling** — `StandardScaler` applied for KNN and Logistic Regression to normalize feature magnitudes

</details>

###  Train-Test Split

```
Total Data: 2,200 samples
🟦 Training Set: 80% → 1,760 samples
🟨 Testing Set:  20% → 440 samples
```

---

##  Exploratory Data Analysis

EDA was performed to understand data characteristics before model development:

| Analysis | Purpose |
|---------|---------|
|  Dataset dimensions | Understand structure and data types |
|  Statistical summary | Describe range and central tendency |
|  Histograms | Understand feature distributions |
|  Boxplots | Detect outliers |
|  Correlation heatmap | Analyze inter-feature relationships |
|  Class distribution | Confirm dataset balance |

###  Key EDA Findings

- ✅ **Balanced dataset** — 22 crops × 100 samples each
- ✅ **No missing values or duplicates**
- ⚠️ **Some outliers** in nutrient & rainfall values — retained as genuine agricultural observations
- 📌 Crop recommendation depends on **combined influence** of multiple parameters, not a single feature
- ✅ Dataset confirmed **clean and ML-ready**

---

## 🤖 Model Development

Three supervised learning algorithms were implemented and compared:

### 1️⃣ Logistic Regression

> A probabilistic linear classifier that estimates crop class probabilities

| ✅ Advantages | ⚠️ Limitations |
|---|---|
| Simple and computationally efficient | Assumes linear decision boundaries |
| Easy to interpret | Performance drops on complex data |
| Strong baseline model | — |

### 2️⃣ K-Nearest Neighbors (KNN)

> Classifies crops by finding the K most similar agricultural samples via Euclidean distance

| ✅ Advantages | ⚠️ Limitations |
|---|---|
| Effective for multi-class classification | Sensitive to feature scaling |
| Captures similarity between conditions | Slow prediction on large datasets |
| No distributional assumptions | — |

> **K values from 1–20 were evaluated** to find the optimal K with highest test accuracy

### 3️⃣ Random Forest  *Best Model*

> An ensemble of decision trees trained on random data subsets; final prediction via majority voting

| ✅ Advantages | ⚠️ Limitations |
|---|---|
| Very high accuracy | Higher compute requirements |
| Handles non-linear relationships | Less interpretable |
| Robust against noise | — |
| Less prone to overfitting | — |

---

##  Results & Evaluation

### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
|  Logistic Regression | 97.27% | 97.40% | 97.27% | 97.25% |
|  K-Nearest Neighbors | 98.18% | 98.28% | 98.18% | 98.17% |
|  **Random Forest** | **99.55%** | **99.57%** | **99.55%** | **99.55%** |

###  Visual Comparison

```
Accuracy Comparison:
─────────────────────────────────────────────────────────────────────
Logistic Regression  ████████████████████████████████████████ 97.27%
KNN                  █████████████████████████████████████████ 98.18%
Random Forest        ████████████████████████████████████████▌ 99.55%
─────────────────────────────────────────────────────────────────────
                     96%                                       100%
```

###  Evaluation Metrics Used

- **Accuracy** — % of correctly classified samples
- **Precision** — Correctness of positive predictions
- **Recall** — Proportion of correctly identified samples
- **F1-Score** — Harmonic mean of Precision and Recall
- **Confusion Matrix** — Per-class prediction analysis

###  Final Model: Random Forest

> Random Forest was selected as the final model with **99.55% accuracy**, the lowest classification errors in the confusion matrix, and excellent generalization performance.

---

##  Conclusion

The **Crop Recommendation System** successfully demonstrates the application of supervised machine learning in precision agriculture. By analyzing soil nutrients (N, P, K), temperature, humidity, pH, and rainfall, the system predicts the most suitable crop with high accuracy.

| Algorithm | Accuracy |
|-----------|----------|
| Logistic Regression | 97.27% |
| KNN | 98.18% |
| **Random Forest** ✅ | **99.55%** |

**Random Forest** emerged as the most effective algorithm due to its ensemble learning approach, high predictive accuracy, and robustness against noise.

###  Future Enhancements

- [1]  Integration of real-time weather data APIs
- [2]  Fertilizer recommendation module
- [3]  Crop disease prediction
- [4]  Market price forecasting
- [5]  Mobile app interface for farmers
- [6]  Region-specific model fine-tuning

---

## 🛠️ Tech Stack

<div align="center">

| Category | Technology |
|----------|-----------|
| **Language** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) |
| **Notebook** | ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white) |
| **Data Manipulation** | ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white) |
| **Visualization** | ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square&logo=python&logoColor=white) ![Seaborn](https://img.shields.io/badge/Seaborn-4C78A8?style=flat-square&logo=python&logoColor=white) |
| **Machine Learning** | ![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) |
| **Dataset Platform** | ![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=flat-square&logo=kaggle&logoColor=white) |

</div>

**Libraries Used:**
- `pandas` — Data loading, manipulation, and analysis
- `numpy` — Numerical computations
- `matplotlib` & `seaborn` — Data visualization and EDA
- `scikit-learn` — ML models, preprocessing, and evaluation
  - `LogisticRegression`
  - `KNeighborsClassifier`
  - `RandomForestClassifier`
  - `StandardScaler`, `LabelEncoder`
  - `train_test_split`, `classification_report`, `confusion_matrix`

---

## 📁 Project Structure

```
 crop-recommendation-system/
│
├──  AI_ML_Internship_Project.ipynb   # Main Jupyter Notebook
├── 📄 README.md                         # Project documentation 
├── 📂 data/
│   └──  Crop_recommendation.csv       # Dataset
└── 📂 results/
    ├──  eda_plots                    # EDA visualizations
    └──  model_results                # Confusion matrices & metrics
    
```

---

## 🚀 How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/AditiParashar19/Minor_Project_1_ML.git
cd Minor_Project_1_ML

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Jupyter Notebook
jupyter notebook AI_ML_Internship_Project.ipynb
```

### Quick Prediction Example

```python
import numpy as np

# Input: [N, P, K, Temperature, Humidity, pH, Rainfall]
sample = np.array([[90, 42, 43, 20.8, 82.0, 6.5, 202.9]])
sample_scaled = scaler.transform(sample)

prediction = rf_model.predict(sample_scaled)
print(f"Recommended Crop: {label_encoder.inverse_transform(prediction)[0]}")
# Output: Recommended Crop: Rice
```

---

##  References

1. Atharva Ingle. [Crop Recommendation Dataset](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset). Kaggle.
2. [Scikit-learn Documentation](https://scikit-learn.org/stable/) 
3. McKinney, W. (2022). *Python for Data Analysis* (3rd Edition). O'Reilly Media.
4. [Pandas Documentation](https://pandas.pydata.org/)  
5. [NumPy Documentation](https://numpy.org/) 
6. [Matplotlib Documentation](https://matplotlib.org/) 
7. [Seaborn Documentation](https://seaborn.pydata.org/) 

---

<div align="center">

**Made with ❤️ for Agriculture**
