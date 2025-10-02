```markdown
# 🚗 Used Car Price Prediction (Pakistan Market)

This project predicts **used car prices** based on scraped data from [Pakwheels](https://www.pakwheels.com/used-cars/).  
It demonstrates the **Data Science workflow**:  
data collection → cleaning → EDA → feature engineering → model building → evaluation.  

---

## 📂 Project Workflow  

### 1. Web Scraping  
- Scraped car listings (title, price, year, mileage, fuel, transmission, engine, etc.)  
- Implemented pagination to scrape multiple pages.  
- Handled failed requests and optimized scraping for Colab environment.  
- Saved raw dataset as CSV for reproducibility.  

### 2. Data Cleaning  
- Removed duplicates & irrelevant columns (e.g., title).  
- Fixed column types (numeric conversion for price, mileage, engine size).  
- Handled missing values:
  - `engine_cc`, `battery_kwh` → imputed with `0` + missingness flag.  
  - No nulls in categorical columns.  
- Handled unrealistic values:
  - Mileage > 1,000,000 km → capped/dropped.  
  - Price spikes for old models (e.g., vintage cars) → handled as outliers.  

### 3. Exploratory Data Analysis (EDA)  
- Distribution plots of price, mileage, year.  
- Price vs Mileage scatterplots → identified depreciation trends.  
- Heatmap of numeric correlations.  
- Grouped analysis:
  - Price variation across **brands** (company).  
  - Price variation across **models**.  
- Detected multicollinearity with correlation & VIF.  

### 4. Feature Engineering  
- **Derived features:**
  - `car_age = CurrentYear - Year`  
  - `price_per_km = Price / Mileage`  
- **Transformations for skewed data:**  
  - Log / Box-Cox for mileage and price.  
- **Encoding:**  
  - One-Hot → fuel, transmission, engine_type, company  
  - Frequency Encoding → model  
- **Scaling:**  
  - RobustScaler for numeric features  

### 5. Modeling  
- Baseline models: Linear, Ridge, Lasso, ElasticNet  
- Tree-based models: Decision Tree, Random Forest  
- Boosting: AdaBoost, XGBoost, LightGBM  
- **Best model:**  
  - **LightGBM (tuned)**  
  - Cross-validated R²: ~0.90  
  - MAE: ~5.1 lacs   

---

## 📊 Results  

| Model              | MAE (↓) | R² (↑) |
|--------------------|---------|--------|
| Linear Regression  | 16.3    | 0.61   |
| Decision Tree      | 7.0     | 0.85   |
| Random Forest      | 7.3     | 0.86   |
| XGBoost            | 5.2     | 0.89   |
| **LightGBM (tuned)** | **5.1** | **0.90** |

---

## ⚙️ Tech Stack  

- **Data Collection:** BeautifulSoup, Requests  
- **Data Processing:** pandas, numpy  
- **EDA & Visualization:** matplotlib, seaborn  
- **Modeling:** scikit-learn, XGBoost, LightGBM    

---

## 📂 Repository Structure  

```

├── data/
│   ├── raw_data.csv
│   └── cleaned_data.csv
├── notebooks/
│   ├── 01_webscraping.ipynb
│   ├── 02_cleaning_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_modeling.ipynb
│   └── 05_deployment.ipynb
├── models/
│   ├── final_lgbm_pipeline.pkl
└── README.md

```
---

## 🔑 Key Learnings  

- Designing end-to-end ML pipelines for real-world data.  
- Handling imbalanced categories (rare companies/models).  
- Encoding strategies for high-cardinality features.  
- Comparing classical regression vs tree-based models.  
- Hyperparameter tuning for boosting algorithms.  

---

## 👨‍💻 Author  

**Basharat Asghar**  
- Data Scientist | ML Enthusiast  
- [LinkedIn](https://www.linkedin.com/in/basharat-asghar) | [GitHub]([https://github.com](https://github.com/Basharat-Asghar))  

---
```
