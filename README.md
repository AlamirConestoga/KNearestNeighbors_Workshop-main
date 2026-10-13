# KNN Workshop: Rainy vs Not-Rainy Weather Classification

## Team Members — Team 5

| Student Name | Student ID |
|---|---|
| Alamir Ibrahim | 9104960 |
| Arya Vinodbhai Patel | 9084843 |
| Asangika Hettiarachchi | 7461502 |
| Preethi Vasudevan Nair | 9125985 |

## 1. Workshop Overview

This workshop explores the K-Nearest Neighbors (KNN) algorithm for classification using Python and scikit-learn.

We first implemented KNN using the Iris dataset to understand how the algorithm works. We then applied KNN to a real-world weather dataset to classify weather conditions as rainy or not rainy.

The workshop also focuses on data preprocessing, exploratory data analysis (EDA), model evaluation, hyperparameter comparison, and modular machine learning pipelines.

## 2. Dataset

We used a CSV dataset named `weather_data.csv`, containing hourly weather information for Berlin, Germany. The weather data was originally obtained from Open-Meteo.

The dataset contains **168 records** with the following attributes:

- `time` — Date and time
- `temperature_2m` — Temperature (°C)
- `relative_humidity_2m` — Relative humidity (%)
- `precipitation` — Precipitation (mm)
- `wind_speed_10m` — Wind speed (km/h)

We created a new target variable called `rainy`:

- **0 — Not Rainy:** Precipitation equals 0
- **1 — Rainy:** Precipitation is greater than 0

### Class Distribution

| Class | Records | Percentage |
|---|---:|---:|
| Not Rainy (0) | 163 | 97.02% |
| Rainy (1) | 5 | 2.98% |
| **Total** | **168** | **100%** |

The dataset is highly imbalanced because most observations represent non-rainy weather.

We use a saved CSV file to ensure consistent results and reproducibility.

## 3. Summary of Our Work

### Part 1: KNN Using the Iris Dataset

We implemented KNN classification using the Iris dataset.

- Loaded the Iris dataset using scikit-learn.
- Split the dataset into training and testing sets.
- Trained a KNN classifier.
- Evaluated model accuracy.
- Visualized Iris species using a scatter plot.
- Highlighted a test data point and its predicted species.

The Iris model achieved **100% accuracy** on the test data used in the workshop.

### Part 2: Weather Data Analysis

We loaded the weather CSV dataset using pandas.

We performed:

- Data inspection and descriptive statistics
- Missing-value and duplicate checks
- Histograms to understand feature distributions
- Boxplots to examine potential outliers
- Rainy versus non-rainy class distribution analysis

### Part 3: Data Cleaning and Feature Engineering

We prepared the weather dataset for KNN classification.

- Converted timestamps into datetime format.
- Checked for invalid and duplicate records.
- Created the binary target variable `rainy`.
- Selected temperature, humidity, wind speed, and time-based features.
- Converted the hour into sine and cosine features to represent the daily cycle.
- Applied median imputation and standard scaling through a scikit-learn Pipeline.
- Split the dataset into training and testing sets using an 80:20 ratio.

Precipitation was excluded from the input features to avoid target leakage.

### Part 4: KNN Model Training and Evaluation

We trained an initial KNN classifier using:

- **K value:** 3
- **Distance metric:** Euclidean

We evaluated the model using accuracy, precision, recall, F1-score, and a confusion matrix.

### Model Performance

| Metric | Euclidean KNN | Manhattan KNN |
|---|---:|---:|
| K Value | 3 | 3 |
| Accuracy | 97.06% | 97.06% |
| Precision | 50.00% | 50.00% |
| Recall | 100.00% | 100.00% |
| F1-score | 66.67% | 66.67% |

Both models achieved the same performance on the test dataset.

However, the test dataset contained only one rainy record. Therefore, these results are not sufficient to conclude that the model will reliably identify rainy conditions in new weather data.

### Part 5: Hyperparameter Comparison

We compared the following KNN configurations:

- **K values:** 3, 5, 7, 9
- **Distance metrics:** Euclidean and Manhattan

We used GridSearchCV with stratified cross-validation and F1-score as the evaluation metric.

All eight configurations produced a cross-validation F1-score of **0.0**.

GridSearchCV reported K = 3 with Euclidean distance, but the results were tied, so no clearly superior configuration was identified.

We also evaluated K = 3 with Manhattan distance as an additional experiment.

### Part 6: Modular ML Pipeline Architecture

We organized our KNN implementation using reusable Python functions following the Machine Learning Pipeline Pattern.

The main functions are:

- `load_data()` — Loads the weather dataset.
- `preprocess_data()` — Prepares the data and performs feature engineering.
- `train_model()` — Creates and trains the KNN pipeline.
- `evaluate_model()` — Evaluates model predictions.

This structure improves readability, reusability, and maintainability.

### Part 7: Additional Model Evaluation

We performed additional analysis to understand model performance.

- Calculated precision, recall, and F1-score manually using confusion matrix values.
- Compared scenarios where precision or recall is more important.
- Evaluated the effect of different decision thresholds.
- Discussed how class imbalance affects model evaluation.

### Part 8: Reflection and Peer Comparison

We answered the workshop reflection questions covering KNN performance, preprocessing, strengths and limitations, unsuitable use cases, and potential MLOps improvements.

We also compared our weather classification project with Team 2's Heart Disease classification project.

Our team used reusable Python functions, while Team 2 implemented an object-oriented approach using classes.

This comparison helped us understand different ways of organizing machine learning workflows and the importance of choosing evaluation metrics appropriate to the dataset.

## 4. Technologies and Libraries

The project uses:

- Python
- Jupyter Notebook
- pandas
- NumPy
- matplotlib
- scikit-learn
- Git and GitHub

## 5. Project Structure

```text
KNearestNeighbors_Workshop/
│
├── data/
│   └── weather_data.csv
│
├──  KNN_Workshop_Solution.ipynb
│
└── README.md
```

The weather CSV is stored separately from the notebook to support reproducibility.

## 6. How to Run the Project

### Step 1: Clone the Repository

```bash
git clone https://github.com/AlamirConestoga/KNearestNeighbors_Workshop-main.git
cd KNearestNeighbors_Workshop
```

### Step 2: Install Required Libraries

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### Step 3: Open the Notebook

Open:

`KNN_Workshop_Solution.ipynb`
/
Using VS Code or Jupyter Notebook.

### Step 4: Run the Notebook

Ensure the working directory is the `notebooks` folder and the dataset is available at:

`../data/weather_data.csv`

Select the correct Python kernel and execute the notebook cells from beginning to end.

The notebook includes model training, visualizations, evaluation results, reflections, and peer comparisons.

## 7. Key Findings

- KNN is a simple algorithm for classification.
- Feature scaling is important because KNN relies on distance calculations.
- Our weather dataset is highly imbalanced, with only 2.98% rainy observations.
- Both evaluated KNN models achieved 97.06% test accuracy.
- Accuracy alone is insufficient to judge performance on imbalanced datasets.
- Precision, recall, F1-score, and confusion matrices provide additional information about model performance.
- A larger dataset with more rainy observations would allow more reliable evaluation.

## 8. Conclusion

This workshop helped us understand the KNN algorithm and its application to real-world classification problems.

We practiced data collection, exploratory data analysis, preprocessing, feature engineering, model training, evaluation, and modular pipeline development.

Although our models achieved high test accuracy, the small number of rainy records limits the reliability of the results.

The workshop also demonstrated the importance of reproducibility, teamwork, documentation, and software engineering practices in machine learning projects.