# 🏡 Airbnb Data Mining Project – Vaud, Switzerland

This repository contains a full-scale data mining analysis of Airbnb listings in the Vaud region of Switzerland. The project applies data preprocessing, exploratory data analysis (EDA), multiple predictive modeling techniques, classification, clustering, and mapping to draw business insights relevant to hosts, platforms, and users.

---

## 📍 Why Vaud?

Vaud offers a mix of urban, suburban, and alpine destinations like Lausanne, Montreux, and Ollon. The diversity in location, seasonality, and listing type provided a rich dataset (75 columns × 5286 rows) suitable for a wide range of machine learning models.

---

## 📊 Project Workflow

### 1. Data Cleaning
- Dropped columns with >40% missing data
- Filled numeric columns with median, reviews with 0
- Converted percentage fields to numeric
- Parsed amenities and created binary features (e.g., `Kitchen_present`)
- Imputed categorical variables with mode or placeholders
- Removed rows with missing target values

### 2. Exploratory Data Analysis (EDA)
- Median price, bedroom counts, and review scores by neighborhood
- Choropleth map of listing prices
- Boxplots of price by room type
- Countplots by room type and location
- WordCloud and mapping keywords by popularity and accessibility

### 3. Predictive Modeling

#### 🔢 Multiple Linear Regression (MLR)
- Goal: Predict listing price
- Applied log transformation to price
- Used 16 key predictors (e.g., accommodates, bathrooms, availability)
- Evaluated using RMSE and R²
- Tested assumptions (VIF, residuals, Breusch-Pagan)

#### 🧩 K-Nearest Neighbors (KNN)
- Goal: Classify presence of kitchen
- Features: 30+ numeric variables
- Preprocessing: Scaling, 80/20 split
- Accuracy: 92%, Recall for class 1: 97%

#### 🤖 Naive Bayes
- Goal: Classify value perception (Low, Medium, High)
- Target: Binned `review_scores_value`
- Model: GaussianNB
- Accuracy: 46%, performed best on High class
- Tested with fictional listing scenario

#### 🌳 Classification Tree
- Goal: Predict `host_response_time`
- Feature importance: acceptance rate, response rate, availability
- Tree-based rules showed booking and listing patterns influence host speed

#### ⚡ XGBoost Classifier
- Same classification goal as decision tree
- Added class weights and hyperparameter tuning (GridSearchCV)
- Outperformed decision tree in balancing all classes

### 4. Clustering (Unsupervised Learning)
- Goal: Segment listings into clusters
- Features: price, reviews, beds, availability
- Engineered: `price_per_person`
- Used KMeans with `k=2`
- Visualized clusters with PCA
- Interpretation:
  - Cluster 0: Premium, high-price, full-home listings
  - Cluster 1: Economy, consistent pricing, shared/private rooms
- Confirmed both clusters have high guest satisfaction

---

## 📌 Tools Used
- Python (Pandas, NumPy, Scikit-learn, Statsmodels, XGBoost)
- Plotly, Seaborn, Matplotlib
- WordCloud, PCA, KBinsDiscretizer
- Google Colab / Jupyter Notebook

---

## 🔍 Key Takeaways
- Airbnb listings with better availability and fair pricing perform best
- Majority of listings have kitchens and earn high reviews
- KNN and XGBoost models perform well on classification tasks
- Clustering reveals two distinct market segments: premium and economy
- Linear regression helps guide pricing strategies for hosts

---
