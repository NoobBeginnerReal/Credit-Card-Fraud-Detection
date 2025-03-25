# 🏦 Credit Card Fraud Analysis I - March 23, 2025
# 📌 Overview

This project analyzes Credit Card fraud risk using real-world financial data to help banks make preventative data-driven decisions. The goal is to develop a predictive yet interpretable model that identifies fraudsters.

We performed Exploratory Data Analysis to understand the relationships between variables and implemented Logistic Regression (baseline), Random Forest and XGBoost to evaluate predictive power between models.

This project utilized basic hyperparameter tuning to improve models' output and performance, class balancing as well as feature importance to draw quick insights.

# 🎯 Problem Statement
Financial institutions face critical risks when lending to individuals who may default. Identifying risky applicants before approval can:

- Reduce non-performing loans
- Improve profitability
- Streamline loan decision processes

This project aims to:

- Analyze key features influencing default.
- Build classification models to predict default risk.
- Optimize for recall to catch more potential defaulters.

# 📂 Dataset
- Source: credit_card_fraud.csv (uploaded manually)
- Contains: date, time, merchant, amount, job, city and state
- Rows: 339,607 credit card transactions
- Target Variable: is_fraud (1 = fraud, 0 = legit)

# 🔧 Methods: Preprocessing and Modelling

✅ Data Preprocessing
- The data is relatively clean so no cleaning required
- Some feature engineering and encoding was done before modelling

⚙️ Feature engineering
- Extracted time features from transaction timestamp (`hour`, `day_of_week`, `month`)
- Calculated `age` from date of birth
- Binned ages into age groups
- Combined `city` + `state` for granular geo-analysis
- Prepped for modeling (to be encoded)

⚙️ Modeling:
- Baseline: Logistic Regression
- Advanced: Random Forest, XGBoost
- Evaluation: Precision, Recall, F1, AUC
 
⚙️ Tuning and Feature Importance
- Performed both GridCV and RandomizedCV for practice purposes to further tune models

# 📊 Logistic Regression Results (Class 1)
 | Metrics  | Value |
| ------------- | ------------- |
| Accuracy  | .89  |
| Precision  | 0.04  |
| Recall  | 0.74 |
| F1 Score  | 0.07  |

# 📊 Random Forest Results (Class 1)
 | Metrics  | Value |
| ------------- | ------------- |
| Accuracy  | 0.99  |
| Precision  | 0.94  |
| Recall  | 0.74 |
| F1 Score  | 0.83  |

✅ Insights:
- Improved precision and accuracy compared to Logistic Regression

# 📊 XGBoost Results (Class 1)
 | Metrics  | Value |
| ------------- | ------------- |
| Accuracy  | 0.99  |
| Precision  | 0.80  |
| Recall  | 0.86 |
| F1 Score  | 0.83  |

✅ Insights:
- Pretty balanced performance but still came short of Random Forest

# 📊 Key EDA Insights

### 1. **Fraud by Category**
- Most frauds occurred in `shopping_pos`, `grocery_pos`, and `gas_transport`
- `shopping_net` and `misc_net` categories had large-value fraud outliers

### 2. **Time-Based Patterns**
- Fraud spikes around midnight and early afternoon
- Late-night fraud (10 PM – 3 AM) shows high activity in online categories

### 3. **Geo Analysis**
- California had the highest fraud volume, but smaller towns had disproportionately high fraud rates
- Cities like Los Angeles, New York, and Chicago dominated in fraud volume

### 4. **Age & Job**
- Fraud most frequent among age 40–60
- Technical professionals (e.g., engineers, analysts) experienced more fraud—likely victims of online compromise

### 5. **Merchant Insights**
- No single merchant dominated fraud, but certain combinations of job + category + time revealed risk patterns

# 🏆 Top XGBoost Feature Highlights:
| Features  | Insights |
| ------------- | ------------- |
| category_gas_transport  | 🚗 Huge fraud signal — maybe due to card skimming at gas stations  |
| amt  | 💵 Transaction size always matters  |
| category_food_dining  | 🍽️ Possibly where fraudsters test cards? |
| category_grocery_net  | 🛒 Online groceries — fraudsters love low-attention merchants  |
| category_travel  | ✈️ Big-ticket fraud target  |
| hour  | ⏰ Time of day — likely helps detect off-hour transactions  |

## 🔍 Key Takeaways
- Common everyday transactions that don't trigger suspicion => Making accurate modelling difficult
- Fraud behavior usually happen during late night (10PM - 3AM)
- Older people (40-60 years old) => likely victims of frauds
- Frauds behavior is a blend of behavioral patterns, demographic and spending context

## Immediate actions
- 🔒 Prioritize Real-Time Monitoring: especially during late nights
- Launch targeted awareness for customers aged 50+

# Model Implementation
- Further model implementation needed to anticipate expected losses
