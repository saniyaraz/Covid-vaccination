# 💉 COVID-19 Vaccination Prediction

A Machine Learning project focused on analyzing COVID-19 vaccination data and estimating vaccination numbers over time.

The project uses global vaccination data and focuses specifically on **Austria** for the modeling task.

---

## 📌 Project Overview

The main goal of this project is to explore COVID-19 vaccination data and build regression models to estimate the total number of vaccinations based on date-related features.

The project covers:

* Exploratory Data Analysis (EDA)
* Missing value analysis
* Data preprocessing
* Feature engineering
* Date transformation
* Data aggregation
* Data scaling
* Data visualization
* Regression modeling
* Model comparison

---

## 📂 Dataset

Two datasets are used in this project:

### `country_vaccinations.csv`

Contains country-level COVID-19 vaccination data with **31,240 records and 15 columns**.

Main features include:

| Feature                               | Description                       |
| ------------------------------------- | --------------------------------- |
| `country`                             | Country name                      |
| `iso_code`                            | Country ISO code                  |
| `date`                                | Vaccination date                  |
| `total_vaccinations`                  | Total number of vaccinations      |
| `people_vaccinated`                   | Number of people vaccinated       |
| `people_fully_vaccinated`             | Number of fully vaccinated people |
| `daily_vaccinations`                  | Daily vaccinations                |
| `total_vaccinations_per_hundred`      | Total vaccinations per 100 people |
| `people_vaccinated_per_hundred`       | Vaccinated people per 100         |
| `people_fully_vaccinated_per_hundred` | Fully vaccinated people per 100   |
| `daily_vaccinations_per_million`      | Daily vaccinations per million    |

The dataset also contains information about vaccine types and data sources.

### `country_vaccinations_by_manufacturer.csv`

Contains vaccination data broken down by vaccine manufacturer, with **9,157 records and 4 columns**:

| Feature              | Description                             |
| -------------------- | --------------------------------------- |
| `location`           | Country/location                        |
| `date`               | Vaccination date                        |
| `vaccine`            | Vaccine manufacturer                    |
| `total_vaccinations` | Total vaccinations for the manufacturer |

---

## 🇦🇹 Project Focus: Austria

After exploring the available countries, **Austria** was selected as the focus of the project.

The selected datasets contain:

* **201 records** for Austria in the country-level dataset
* **112 records** for Austria in the manufacturer-level dataset

---

## 🔎 Exploratory Data Analysis

The EDA section includes:

* Dataset shape and structure
* Data types
* Missing value analysis
* Statistical summaries
* Duplicate checking
* Unique country and vaccine values
* Feature inspection

The initial analysis showed a considerable number of missing values in several vaccination-related features.

Both datasets were also checked for duplicate rows, with no duplicates found.

---

## 🧹 Data Preprocessing

Several preprocessing steps were performed to prepare the data for regression models.

### 1. Selecting Austria

Only records corresponding to Austria were selected from both datasets.

```python
X = df1.loc[df1['country'] == 'Austria']
Y = df2.loc[df2['location'] == 'Austria']
```

---

### 2. Selecting Relevant Features

The modeling dataset was simplified to focus on:

* `total_vaccinations`
* `year`
* `month`
* `day`

The manufacturer-level dataset was aggregated because vaccination counts were separated by vaccine type.

---

### 3. Date Feature Engineering

The original `date` column was converted to datetime and separated into:

```text
year
month
day
```

This allows regression models to work with numerical date-related features.

---

### 4. Aggregating Vaccination Data

Since the manufacturer dataset contains separate vaccination counts for different vaccine types, the values were aggregated by date:

```python
Y_new = Y_new.groupby(
    ['year', 'month', 'day'],
    as_index=False
).agg({
    'total_vaccinations': 'sum'
})
```

This produces a single total vaccination value for each date.

---

## 📊 Visualization

The project includes a **Storytelling / Visualization** section to explore vaccination trends and patterns in the selected data.

Visualization is used as part of the exploratory process before applying regression models.

---

## 🤖 Machine Learning Models

The notebook imports and works with several regression algorithms:

1. Linear Regression
2. Polynomial Regression
3. Support Vector Regression (SVR)
4. Decision Tree Regression
5. Random Forest Regression

The project also imports TensorFlow for potential neural-network-based modeling.

---

## 🎯 Prediction Task

The main prediction task can be summarized as:

```text
Date
 ↓
Year + Month + Day
 ↓
Regression Model
 ↓
Estimated Total Vaccinations
```

The objective is to estimate the number of vaccinations using the temporal features extracted from the vaccination records.

---

## 🛠️ Technologies & Libraries

The project was implemented in Python using:

* Python
* NumPy
* Pandas
* Matplotlib
* Seaborn
* Scikit-learn
* TensorFlow

Main Scikit-learn tools used include:

* `StandardScaler`
* `SimpleImputer`
* `LinearRegression`
* `PolynomialFeatures`
* `SVR`
* `DecisionTreeRegressor`
* `RandomForestRegressor`

---

## 📁 Project Structure

```text
.
├── Project1.ipynb
├── country_vaccinations.csv
├── country_vaccinations_by_manufacturer.csv
└── README.md
```

> Dataset files may be omitted from the repository depending on their original source and licensing conditions.

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

### 2. Install the required libraries

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
```

### 3. Open the notebook

```bash
jupyter notebook
```

Then open:

```text
Project1.ipynb
```

Run the notebook cells sequentially.

---

## 📌 Key Takeaways

This project provided practical experience with a complete regression workflow:

```text
Raw Data
   ↓
Data Exploration
   ↓
Missing Value Analysis
   ↓
Data Selection
   ↓
Feature Engineering
   ↓
Date Transformation
   ↓
Data Aggregation
   ↓
Scaling
   ↓
Visualization
   ↓
Regression Modeling
```

The project focuses on **Austria's COVID-19 vaccination data** and uses date-based features to estimate total vaccination counts.

---

## 🔮 Possible Improvements

Future improvements could include:

* More advanced time-series feature engineering
* Using rolling and lag features
* Time-series-specific validation
* Hyperparameter tuning
* Comparing additional regression models
* More detailed visualization of vaccination trends
* Using a dedicated time-series forecasting approach
* Evaluating models with multiple regression metrics

---

## 👤 Author

**Saniyar**

Machine Learning Project — COVID-19 Vaccination Data Analysis & Regression
