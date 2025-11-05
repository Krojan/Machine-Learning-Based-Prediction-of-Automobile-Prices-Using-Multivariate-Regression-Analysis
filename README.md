# Machine Learning–Based Prediction of Automobile Prices Using Multivariate Regression Analysis

## Abstract
Developed a predictive modeling framework to estimate automobile prices using statistical and machine learning techniques. Conducted data preprocessing, feature selection, and regression modeling with Linear and SGD Regressors to analyze the impact of technical and design attributes on market value. . Comparative experiments employing Ordinary Least Squares (Linear Regression) and Stochastic Gradient Descent (SGD) models demonstrate that brand information and engine-related parameters significantly improve predictive accuracy highlighting the effectiveness of feature engineering in data-driven price estimation.

---

## Methodology

The analytical workflow consisted of five key stages:

### 1. Data Acquisition and Preprocessing
- Imported the *[Car Price Assignment](https://www.kaggle.com/datasets/hellbuoy/car-price-prediction)* dataset containing 205 automobile records and 26 attributes.  
- Performed data cleaning, missing-value checks, and normalization of categorical labels.  
- Parsed brand names from the *CarName* attribute for use in categorical encoding.

### 2. Exploratory Data Analysis (EDA)
- Conducted correlation and distribution analyses using *seaborn* and *matplotlib* to examine relationships between engine specifications, body type, and price.  
- Identified key positive correlations for `enginesize`, `horsepower`, and `curbweight`.

### 3. Feature Engineering
- Encoded categorical features via one-hot encoding.  
- Standardized numerical variables using *StandardScaler* to stabilize optimization.  
- Generated both **brand-inclusive** and **brand-excluded** feature sets to isolate the effect of brand perception.

### 4. Model Construction
- Implemented two regression models:
  - **Linear Regression (OLS):** Analytical closed-form optimization.  
  - **SGD Regressor:** Iterative gradient-based optimization for scalability and regularization.  
- Split the dataset into 80% training and 20% testing partitions.

### 5. Evaluation Metrics
- Model performance was evaluated using:
  - **Mean Absolute Error (MAE)**
  - **Mean Squared Error (MSE)**
  - **Root Mean Squared Error (RMSE)**
  - **Coefficient of Determination (R²)**

---

## Observations
- **Engine-related variables** (`enginesize`, `horsepower`, `cylindernumber`, `enginetype`) exhibited the highest positive correlation with automobile price, confirming their role as primary determinants of market valuation. Engine size showed the highest correlation with price (r ≈ 0.87), making it the primary determinant of market value.
- **Categorical brand encoding** substantially improved predictive accuracy, indicating that price differences among manufacturers are not solely explained by measurable specifications. Among categorical variables, brand and fuel type were key differentiators: premium brands (e.g., BMW, Porsche, Alfa Romero) maintained prices higher than economy brands.  
- Regression coefficients aligned closely with correlation trends, suggesting that the model’s learned feature weights reflect underlying economic relationships.  

---

## Results and Comparisons

### Linear Regression (OLS)

| Model | MAE | MSE | RMSE | R² |
|--------|--------|--------|--------|--------|
| **With Brand Encoding** | 1905.82 | 5.07×10⁶ | 2252.16 | **0.934** |
| **Without Brand** | 2372.20 | 9.24×10⁶ | 3039.87 | **0.880** |

**Observation:**  
Including brand information improved the R² score by approximately **5.4%** and reduced MAE by **~20%**, confirming that brand identity captures essential latent market information beyond mechanical attributes.

---

### Stochastic Gradient Descent (SGD) Regression

| Model | MAE | MSE | RMSE | R² |
|--------|--------|--------|--------|--------|
| **With Brand Encoding** | 2046.41 | 6.97×10⁶ | 2639.87 | **0.909** |z
| **Without Brand** | 2386.22 | 1.06×10⁷ | 3255.99 | **0.862** |

**Observation:**  
Brand inclusion led to a **5% R² improvement** and reduced MAE by nearly **14%**. Even with stochastic optimization, brand-level encoding consistently enhanced generalization, confirming its robustness across optimization paradigms.

---

### Comparative Summary

| Model Type | Brand Encoding | ΔR² | ΔMAE (%) 
|-------------|----------------|------|-----------
| Linear Regression | ✅ Included | +0.054 | −20% |
| SGD Regressor | ✅ Included | +0.047 | −14% |

---

## Discussion
The comparative analysis across OLS and SGD models confirms that **brand identity acts as a high-impact categorical determinant** of automobile price, complementing numerical predictors such as engine size, engine type and cylinder number. Feature importance derived from regression coefficients aligned with correlation analysis — engine size, and brand accounting for most fluctuations in price. This validates that market valuation is a multivariate function of both technical performance and perceived brand equity.  
The findings highlight the critical role of **feature engineering and standardization** in improving regression-based inference in econometric datasets.

---

## Conclusion
This study demonstrates that integrating categorical brand attributes alongside engineered numerical features significantly enhances the predictive capacity of regression-based learning models. Both OLS and SGD frameworks achieved high explanatory power (R² ≈ 0.90–0.93), confirming the robustness of multivariate regression for automobile price prediction. The results underscore the broader applicability of statistical learning in modeling real-world pricing systems. Overall, this project exemplifies reproducible data-driven modeling for automated valuation frameworks.
