# 🚗 Used Car Price Prediction - Regression Problem

**Used-Car-Price-Prediction** is a Python-based project designed to predict **used car prices** using regression techniques. It leverages **data preprocessing, feature engineering, exploratory data analysis (EDA), and machine learning models** to estimate car prices based on features like brand, model year, mileage, engine specifications, and accident history. The project tackles challenges like overfitting and data leakage to improve model generalization.

---

## 📊 Dataset

The **Used Car Price Prediction Dataset** is sourced from [Kaggle](https://www.kaggle.com/datasets/taeefnajib/used-car-price-prediction-dataset/data) and extracted from [Cars.com](https://www.cars.com). It contains **4,009 vehicle listings** with **9 features**:

### 📚 Features Description

| Feature            | Description                                                         |
| ------------------ | ------------------------------------------------------------------- |
| `Brand`            | Vehicle brand and model name (e.g., Ford, Hyundai).                 |
| `Model Year`       | Manufacturing year, used to compute `Vehicle_Age`.                  |
| `Mileage`          | Distance driven, indicating wear and tear.                          |
| `Fuel Type`        | Gasoline, diesel, electric, or hybrid                               |
| `Engine Type`      | Engine specs (e.g., horsepower, displacement)                       |
| `Transmission`     | Automatic, manual, or other variants.                               |
| `Exterior Colors`  | Aesthetic details.                                                  |
| `Interior Colors`  | Aesthetic details.                                                  |
| `Accident History` | Whether the vehicle has reported accidents/damage.                  |
| `Clean Title`      | Indicates if the vehicle has a clean title, affecting resale value. |
| `Price`            | Target variable (log-transformed to handle skewness).               |

The dataset requires preprocessing to handle missing values, encode categorical features (e.g., target encoding for `brand`), remove outliers (using 1.5\*IQR), and scale features for models like SVR.

---

## 💻 Code Structure

The project is implemented in a Jupyter Notebook (`app.ipynb`) with the following workflow:

1. **Data Loading**: Load the dataset from a CSV file.
2. **EDA**: Inspected structure, Checked for missing values and duplicates.
3. **Preprocessing**:
   - Handle missing values.
   - Remove outliers using 1.5\*IQR on numerical features.
   - Encode categorical features (e.g., target encoding for `brand`, label encoding for `fuel_type`).
   - Apply `StandardScaler`.
4. **Feature Engineering**:
   - Create `Vehicle_Age` (from `model_year`).
   - Derive `Mileage_per_Year` (`milage` / `Vehicle_Age`).
   - Extract `hp`, `engine displacement` from `engine`.
5. **Modeling**:
   - **Linear Regression**: Baseline model to capture linear relationships, trained on scaled features.
   - **Random Forest Regressor**: Tuned with `GridSearchCV` (e.g., `max_depth=[8, 10, 12]`, `max_features='sqrt'`) and 5-fold `KFold`.
   - **SVR**: Tuned with `GridSearchCV` (e.g., `C=[0.1, 1, 10, 100]`, `kernel=['rbf', 'linear']`) and 5-fold `KFold`.
   - **XGBoost Regressor**: Tuned for high performance.
6. **Evaluation**: Use MAE, RMSE, and R² to assess model performance, with a focus on reducing overfitting (train/test R² gap).

---

## 🚀 Key Features

- Predicts **used car prices** using advanced regression models
- Performs **data preprocessing** (outlier removal, categorical encoding, missing value handling)
- Conducts **EDA** with visualizations (histograms, heatmaps, scatter plots, feature importance)
- Implements **feature engineering** (e.g., `Vehicle_Age`, `hp_per_litre`, `brand_encoded`)
- Evaluates models with **MAE**, **RMSE**, and **R² Score** using 7-fold cross-validation
- Saves results for easy analysis and comparison

---

## 📂 How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/EhsanSamy/Used-Car-Price-Prediction.git
   ```

2. Run the Jupyter Notebook:

   ```bash
   jupyter notebook used-car-price-prediction.ipynb
   ```

3. Check the output:
   - Visualizations (e.g., feature importance, correlation heatmaps) and model results are displayed in the notebook
   - Processed dataset and predictions are available in the notebook environment

---

### ✅ Models Trained & Compared

| Model                    | Test RMSE | Test R²  | perdict          |
|--------------------------|-----------|----------|------------------|
| Linear Regression        | ~10770.80 | 0.66     | Overfitting ❌   |
| Random Forest            | ~9446.60  | 0.77     | Good ✅          |
| Support Vector Regressor | ~9756.67  | 0.76     | Good ✅          |
| XGBoost                  | ~8176.96  | 0.83     | Best ✅✅        |

**XGBoost** showed the best performance, achieving the lowest RMSE, the highest R² which reflects superior accuracy and generalization.

---

## 📌 Why This Project?

Manually predicting used car prices or analyzing automotive data is **time-consuming and complex**. This project **automates the process**, providing a streamlined workflow for researchers, data scientists, and automotive professionals to **predict prices** and **understand key factors** like mileage, brand, and accident history influencing car values.

---
## 🙏 Acknowledgments

This project was developed as part of the **AI Workshop Graduation Project**.  
Special thanks to the instructors and teammates for their guidance and support throughout the journey.

---

## 🔗 Connect with Me

- 💼 [LinkedIn](https://www.linkedin.com/in/ehsan-samy/)
- 📧 [Gmail](mailto:ehsansamy9@gmail.com)
- 🗃️ [Kaggle](https://www.kaggle.com/ehsansamy)
