# 🏠 01 — House Price Prediction with Machine Learning

Introduction to supervised machine learning for A-level students, using Python and
**scikit-learn** to predict house prices from neighbourhood and property features.
The workshop includes a California dataset and a **London borough dataset** so
students can relate the models directly to their own city.

---

## 📁 Folder Contents

| File | Type | Description |
|------|------|-------------|
| `alevel_house_price_prediction.ipynb` | Notebook | Main tutorial and London extension |
| `california_housing.csv` | Data | 2,000 synthetic California neighbourhood records |
| `london_housing.csv` | Data | 1,500 synthetic London property sales across 20 boroughs |

> ⚠️ Keep all three files in the same folder — the notebook loads the CSV files
> by filename from the working directory.

---

## 📖 What You Will Learn

### Part 1 — What is Machine Learning?

**Supervised learning** is a technique where a computer learns a mathematical
relationship between inputs and an output from labelled examples — without
being explicitly programmed with rules.

Today's model learns:

$$\text{House Price} = w_1 \times \text{Income} + w_2 \times \text{Rooms} + w_3 \times \text{Age} + \ldots + b$$

This is **Linear Regression** — the same $y = mx + c$ from A-level Maths, extended
to many input variables simultaneously.

### Part 2 — The Datasets

**California dataset** — 2,000 neighbourhood records:

| Feature | Description |
|---------|-------------|
| `MedInc` | Median household income (×$10k) |
| `HouseAge` | Average age of houses in years |
| `AveRooms` | Average number of rooms per house |
| `AveBedrms` | Average number of bedrooms per house |
| `Population` | Number of people in the neighbourhood |
| `AveOccup` | Average number of people per household |
| `Latitude` | Geographic latitude |
| `Longitude` | Geographic longitude |
| `HouseValue` | 🎯 Target — median house value (USD) |

**London dataset** — 1,500 property sales across 20 boroughs:

| Feature | Description |
|---------|-------------|
| `Borough` | London borough (e.g. Hackney, Camden, Westminster) |
| `Bedrooms` | Number of bedrooms |
| `Bathrooms` | Number of bathrooms |
| `FloorArea` | Property size in m² |
| `PropertyAge` | Construction period (Pre-1900 → Post-2000) |
| `Price` | 🎯 Target — sale price in £ |

London borough median prices (approximate, for reference):

| Borough | Approx. Median |
|---------|---------------|
| Kensington & Chelsea | £950,000 |
| Westminster | £820,000 |
| Hammersmith & Fulham | £720,000 |
| Hackney | £560,000 |
| Newham | £420,000 |
| Barking & Dagenham | £360,000 |

### Part 3 — The Machine Learning Pipeline

```
Raw Data → Exploration (EDA) → Preprocessing → Train/Test Split
    → StandardScaler → LinearRegression → Evaluation → Prediction
```

Key concepts introduced at each stage:

| Step | Concept | A-level connection |
|------|---------|-------------------|
| EDA | Histograms, scatter plots, correlation | Statistics — $r$ values |
| Train/test split | Avoiding data leakage | Exam analogy — don't revise the exam paper |
| StandardScaler | Normalisation | Mean and standard deviation |
| LinearRegression | Weights and intercept | $y = mx + c$ |
| R² score | Goodness of fit | Coefficient of determination |
| RMSE | Prediction error in real units | Root mean square error |

### Part 4 — London Extension

The second half of the notebook retrains **the same `LinearRegression` model**
on London data, introducing:

- **One-hot encoding** — converting borough names (text) into numerical columns
- **Categorical features** — property age bands (Pre-1900, Post-2000, etc.)
- **Feature importance** — which borough commands the biggest price premium?
- **Comparative analysis** — does the same algorithm behave differently on
  London vs California data?

### Part 5 — Interactive Prediction

Two "predict your own" cells let students input property features and receive
an instant price prediction:

- 🏠 **California cell** — input income level, rooms, location coordinates
- 🏙️ **London cell** — input borough, bedrooms, floor area, property age;
  output is compared to the borough median so students get contextual feedback

---

## 🗂️ Notebook Structure

| Section | Content |
|---------|---------|
| 1 | What is Machine Learning? — plain English introduction |
| 2 | Loading tools — imports with summary table |
| 3 | Loading and inspecting the California dataset |
| 4 | Exploratory Data Analysis — price distribution, scatter plots, correlation heatmap |
| 5 | Preprocessing — train/test split, StandardScaler |
| 6 | Training the Linear Regression model |
| 7 | Model evaluation — MAE, RMSE, R², actual vs predicted plot |
| 8 | 🏠 Predict your own California house |
| 9 | 🇬🇧 London extension — load data, one-hot encode, retrain |
| 10 | London model evaluation and feature importance |
| 11 | 🏙️ Predict a London house price |
| 12 | Discussion questions and next steps |

---

## 💬 Discussion Questions

The notebook ends with questions designed to prompt critical thinking:

1. Why is it difficult to predict house prices exactly, even with a perfect algorithm?
2. What features are missing from our dataset that would probably affect price?
3. What was the most important feature in California vs London — and why do they differ?
4. If a bank used an ML model to assess mortgage risk by borough, what ethical
   problems could arise?
5. Linear regression assumes a straight-line relationship. Can you think of cases
   where that fails for house prices?

---

## ⚙️ Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

---

## 🎓 Context

These notebooks were developed for the **AI Literacy Project** taster day
workshops at **Queen Mary University of London**, Department of Chemistry.
They are designed for A-level students with no prior Python experience.

Taster day participants will leave able to:
- Load and explore a real-world dataset using `pandas`
- Train and evaluate a machine learning model using `scikit-learn`
- Interpret model coefficients and understand feature importance
- Predict house prices for properties they design themselves
- Discuss the ethical implications of algorithmic decision-making

---

## 📚 Further Reading

- [scikit-learn documentation](https://scikit-learn.org/stable/modules/linear_model.html)
- [Kaggle — House Prices competition](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
- [Towards Data Science — Linear Regression explained](https://towardsdatascience.com/linear-regression-detailed-view-ea73175f6e86)
- UK House Price Index: [landregistry.data.gov.uk](https://landregistry.data.gov.uk/)
