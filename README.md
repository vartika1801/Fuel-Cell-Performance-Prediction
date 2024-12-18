# Fuel Cell Performance Prediction
This repository contains code to preprocess and build predictive models for a fuel cell performance dataset. The primary goal is to:
1. Select the correct target column based on the "roll number" based selection function.
2. Clean, preprocess, and transform the dataset.
3. Split the dataset into training and test sets (70/30).
4. Run multiple regression models using PyCaret to find the best-performing model.
5. Evaluate the selected model on the test set using standard regression metrics.

# Dataset Description
1. Features (F1, F2, ..., F15):
Various numerical input features that influence fuel cell performance.
2. Targets (Target1, Target2, Target3, Target4, Target5):
Multiple potential target columns. The correct target is selected based on the last digit of the roll number:
Roll number ends in 0 or 5 → Target1
Roll number ends in 1 or 6 → Target2
Roll number ends in 2 or 7 → Target3
Roll number ends in 3 or 8 → Target4
Roll number ends in 4 or 9 → Target5
After determining which target applies to a given row, all other target columns are dropped, leaving a single Target column for modeling.

# Prerequisites
1. Python 3.x
2. Jupyter Notebook or Google Colab environment recommended
3. PyCaret for model training and evaluation
4. Standard Python libraries: pandas, numpy, matplotlib, seaborn, scikit-learn

# Steps Performed by the Code
**1. Data Loading:**
Reads the dataset from the specified CSV file.
**2. Preprocessing:**
Fills missing numeric values with the mean.
Selects only numeric columns for modeling.
If any columns are objects and can be numerically coerced, they are converted.
Optional: Plots histograms and a correlation heatmap for exploratory data analysis.
**3. Target Selection Logic:**
Assigns a pseudo-roll number based on the DataFrame index.
Uses the last digit of this pseudo-roll number to decide which TargetN column to use.
Creates a single Target column and drops the other target columns.
**4. Modeling with PyCaret:**
Sets up a regression environment with PyCaret.
Compares multiple regression models (e.g., Linear Regression, Random Forest, XGBoost, etc.) based on their R² scores.
Selects the top-performing models and displays their performance metrics.
**5. 70/30 Train-Test Split:**
Splits the dataset into 70% training and 30% testing using train_test_split.
Finalizes the best model from the comparison step.
**6. Evaluation on the Test Set:**
Uses the finalized model to make predictions on the test data.
Prints out performance metrics like R², RMSE, and MAE to evaluate model performance.

# Results and Interpretation
1. The code outputs a comparison table of different models evaluated using PyCaret.
2. A bar plot shows Model vs. R² for quick visual comparison.
3. After finalizing the best model, the code predicts on the test set and provides metrics to indicate how well the model generalizes to unseen data.

