# 🚗 UrbanRide ML Forecasting Pipeline

### End-to-End Time Series Demand Prediction for Car Rentals

---

## 📌 Overview

This project tackles a real-world problem:
**How can we accurately predict car rental demand using messy, operational data?**

Instead of relying on clean, ideal datasets, this project works with **noisy, inconsistent, and incomplete data**, simulating real industry conditions.

The goal was not just to build a model — but to design a **robust, production-style machine learning pipeline** that handles:

* Data cleaning at scale
* Feature engineering for time-series data
* Model experimentation and comparison
* Reliable evaluation without data leakage

---

## 🎯 Problem Statement

Car rental businesses need to predict demand to:

* Optimize fleet allocation
* Reduce idle vehicles
* Improve revenue and customer satisfaction

The challenge:
The dataset contains **missing values, inconsistent formats, and mixed data types**, making it unsuitable for direct modeling.

---

## 🧠 Approach & Story

This project evolved through multiple iterations — each solving a real issue found in previous versions.

### 1. 🧹 Data Cleaning (The Hard Reality)

The raw dataset contained:

* Non-numeric values (`$`, `USD`, text labels like *"hot"*, *"cold"*)
* Missing dates and corrupted entries
* Inconsistent categorical values (`Yes`, `Y`, `True`, etc.)

Key steps:

* Custom numeric cleaning using regex
* Median-based imputation for stability
* Standardization of categorical variables
* Handling invalid/missing dates

👉 Result: A **consistent and model-ready dataset**

---

### 2. 🏗 Feature Engineering (Where the Real Value Was Created)

This is where the project becomes strong.

#### ⏳ Time-Based Features

* Month, day, weekday
* Weekend detection

#### 🔁 Lag Features

* `rentedcars_lag1`, `lag2`, `lag3`, `lag7`, `lag15`, `lag30`

These capture **temporal dependencies**, which are critical in forecasting.

#### 📊 Rolling Statistics

* Rolling mean (3-day, 7-day)
* Rolling standard deviation

👉 These features help the model understand **trends, seasonality, and volatility**

---

### 3. 🔄 Encoding & Data Transformation

* Label encoding for categorical variables
* One-hot encoding for improved model performance
* Removal of irrelevant columns (`rentalid`, raw date where needed)

---

### 4. ⚠️ Critical Learning: Time-Series Split

Initial models performed poorly due to **random train-test splitting**.

✔ Fixed by implementing:

* **Chronological split (train → past, test → future)**

👉 This eliminated **data leakage** and dramatically improved model reliability.

---

### 5. 🤖 Model Training

Model used:
**XGBoost Regressor**

Why?

* Handles non-linear relationships well
* Robust to feature scaling
* Works great with tabular data

---

### 6. 🧪 Experimentation

Multiple datasets and approaches were tested:

| Version | Key Idea                                                 |
| ------- | -------------------------------------------------------- |
| d5      | Clean baseline dataset                                   |
| d6      | Removed lag features (performance drop observed)         |
| d7      | Added rolling + extended lag features (best performance) |

👉 This clearly showed:
**Feature engineering > model complexity**

---

### 7. ⚙️ Hyperparameter Tuning

Final model improvements included:

* Lower learning rate
* Increased estimators
* Regularization (L1 + L2)
* Controlled tree depth

👉 Result: Better generalization and stability

---

## 📈 Results

The final model achieved:

* ✅ Strong R² score (significant improvement from initial negative scores)
* ✅ Lower MAE and RMSE
* ✅ Stable predictions on unseen future data

Most importantly:

> The model became **trustworthy**, not just accurate.

---

## 📊 Visualizations

* Demand trends over time
* Correlation heatmaps
* Feature relationships

These helped validate assumptions and guide feature engineering.

---

## 🧰 Tech Stack

* Python
* Pandas, NumPy
* Scikit-learn
* XGBoost
* Matplotlib, Seaborn

---

## 🚀 Key Takeaways

This project highlights real-world ML lessons:

* Data cleaning is more important than modeling
* Time-series problems require special handling
* Feature engineering drives performance
* Avoiding data leakage is critical
* Iteration and experimentation are essential

---

## 💼 Why This Project Matters

This is not just a model — it’s a **simulation of real industry workflow**:

* Handling messy data
* Building reproducible pipelines
* Debugging poor model performance
* Improving through experimentation

---

## 🔮 Future Improvements

* Deploy as a real-time prediction API
* Add deep learning models (LSTM)
* Automate pipeline using Airflow
* Integrate external features (weather, events)

---

## 👨‍💻 Author

Built as a hands-on machine learning project focused on **practical problem-solving and real-world readiness**.

---

## ⭐ Final Note

This project demonstrates the ability to go beyond tutorials and:

✔ Work with messy data
✔ Think critically about modeling decisions
✔ Build end-to-end ML systems

---
