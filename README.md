# KNN Workshop: Rainy vs Not-Rainy Weather Classification

**Name:** Alamir Ibrahim
          Arya Vinodbhai Patel
          Asangika Hettiarachchi
          Preethi Vasudevan Nair

          Arya Vinodbhai Patel
---

**Student ID:** 9104960


                9125985
---
## Summary of My Work

This workshop applies the K-Nearest Neighbours (KNN) algorithm to a real-world weather dataset. The goal is to classify each hour as rainy or not rainy.

1. **Data acquisition:** I loaded 168 hourly weather records (temperature, humidity, precipitation, wind speed) from the Open-Meteo API into a Pandas DataFrame.
2. **Exploratory data analysis:** I checked data types, missing values and duplicates, then used descriptive statistics, histograms and boxplots to understand the data and its outliers.
3. **Target and class balance:** I created a `rainy` label from precipitation (0 = not rainy, 1 = rainy). About 11% of records are rainy, so the dataset is imbalanced.
4. **Preprocessing:** I removed invalid and duplicate records, created sine/cosine time features, and split the data into training and test sets.
5. **Model training:** I built a scikit-learn pipeline (median imputer, standard scaler, KNN) and trained a baseline model with K = 3 and Euclidean distance.
6. **Evaluation:** I evaluated models with accuracy, precision, recall, F1-score and confusion matrices, because accuracy alone is misleading on imbalanced data.
7. **Hyperparameter comparison:** I compared K = 3, 5, 7, 9 and Euclidean vs Manhattan distance using stratified cross-validation on F1-score.
8. **Modular pipeline:** I reorganised the workflow into reusable functions (load, preprocess, train, evaluate).
9. **Final model analysis:** I evaluated the final model, calculated precision, recall and F1 manually from the confusion matrix, discussed real-world cases where precision or recall matters more, and showed how changing the decision threshold trades one against the other.

## Files

- `KNN_Workshop_Solution.ipynb`: the full notebook with all steps, code and observations.
- `README.md`: this file.
