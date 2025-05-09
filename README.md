# 🏡 Airbnb Data Mining Project – Vaud, Switzerland

This repository contains a full-scale data mining analysis of Airbnb listings in the Vaud region of Switzerland. The project applies data preprocessing, exploratory data analysis (EDA), multiple predictive modeling techniques, classification, clustering, and mapping to draw business insights relevant to hosts, platforms, and users.

---

## 📍 Why Vaud?

Vaud is one of Switzerland’s most diverse and scenic cantons, with a strong mix of urban (Lausanne, Montreux), suburban, and rural areas. It offers rich Airbnb data (75 columns × 5,000+ rows), ideal for modeling variability in price, amenities, availability, and guest satisfaction.

---

## 🧹 1. Data Preparation

- Removed columns with >40% missing data (e.g., `license`, `host_about`)
- Imputed numeric features with **median**, review-related features with **0**
- Converted percentage strings to floats (e.g., host response rate)
- Created engineered feature: `price_per_person = price / (accommodates + 1)`
- Standardized all numerical features using `StandardScaler`

Final cleaned dataset: **3,041 rows × 69 columns**

---

## 📊 2. Exploratory Data Analysis (EDA)

We explored listing behavior by neighborhood:

- Median price by top 10 neighborhoods (e.g., Ollon, Lausanne)
- Room types and property type counts
- Review score distributions
- Availability and seasonal trends

### 📌 Visualizations:
- Choropleth map of prices  
- Boxplot of price by room type  
- Countplot of room type by district  
- WordCloud from neighborhood descriptions  
- Bubble chart of availability vs price (bubble size = reviews)

---

## 🧠 3. Predictive Modeling

### 🔹 Multiple Linear Regression (MLR)

- **Goal**: Predict price (CHF) from listing & host features
- Selected top 16 correlated predictors (e.g., `accommodates`, `bathrooms`, `availability_365`)
- Applied log transformation on price
- Final model metrics:
  - R²: **0.591**
  - RMSE: **113.12 CHF**
- OLS summary, VIF scores, residual & QQ plots included
- Tested model on a **sample fictional listing** to validate predictions

---

## 🧪 4. Classification Models

### 📍 A. K-Nearest Neighbors (KNN)

- **Goal**: Predict whether a listing has a `Kitchen`
- Target: `Kitchen_present` = 1 or 0
- Used 30+ numeric predictors (e.g., price, availability, reviews)
- K value: **7** (best accuracy)
- Results:
  - Accuracy: **91%**
  - Precision/Recall for Kitchen-present: 93% / 97%
  - Compared to naive benchmark: **KNN provided better class balance**

### 📍 B. Naive Bayes

- **Goal**: Predict guest **value perception**
- Target: Binned `review_scores_value` into 3 levels (low, medium, high)
- Removed all review-related predictors to avoid leakage
- Used `GaussianNB`
- Accuracy: **46%**
- Model struggled with Low/Medium boundary but captured "High" well
- Evaluated with confusion matrix and tested on a sample listing

---

## 🔀 5. Clustering (K-Means)

- **Goal**: Segment listings into similar groups
- Used KMeans with PCA for 2D visualization
- Engineered feature: `price_per_person`
- Best k = 2 (from Elbow method)

### 📌 Cluster Insights:
- **Cluster 0**: Diverse Premium Rentals
  - High prices, luxury properties, often Entire Homes
- **Cluster 1**: Standard Economy Rentals
  - Lower prices, Private or Shared rooms

### 📈 Visuals:
- PCA Scatterplot of Clusters
- Boxplot (Price by Cluster & Room Type)
- Bar chart (Room Type per Cluster)
- Violin plot (Review Scores per Cluster)

---

## 🛠 Tools & Libraries

- Python (Pandas, NumPy, Scikit-learn, Statsmodels)
- Plotly, Seaborn, Matplotlib
- WordCloud, KBinsDiscretizer
- Google Colab / Jupyter Notebook

---

## 💡 Key Takeaways

- **KNN outperformed naive classifier** by handling both classes well
- **Clustering revealed distinct rental segments**: luxury vs budget
- **Linear regression achieved R² ≈ 0.59**, providing solid price predictions
- **Popular and affordable listings** showed highest engagement
- Listings near **Lake Geneva & ski towns** were high-priced and high-demand

---

## 👨‍💻 Team Members

- Moiz Deshmukh  
- Prabu Jeyabalan  
- Jitvan Vij  

---

## 📌 License

This project is for academic use under Boston University’s AD699 – Data Mining for Business Analytics.

