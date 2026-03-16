# Designing Reproducible ML Experiments (Simple Explanation)

In Machine Learning, **reproducibility** means that **someone else (or even you in the future) can run the same experiment and get the same results**.

This is very important in ML because models depend on:
- Data
- Code
- Hyperparameters
- Libraries
- Random seeds

If these things are not tracked properly, the results **cannot be reproduced**.

---

# 1. What is Reproducibility?

Reproducibility means **being able to repeat an experiment and obtain the same results**.

### Why Reproducibility is Important

- Builds **trust in the model**
- Ensures **accuracy and reliability**
- Reduces **bias in experiments**
- Makes **collaboration easier**
- Helps **debug models**

### Example

Suppose you trained a model and got **91% accuracy**.

If another engineer runs your project and gets **85% accuracy**, something is wrong.

Possible reasons:
- Different dataset
- Different hyperparameters
- Different library versions
- Different random seed

Reproducibility ensures **everyone gets the same results**.

---

# 2. MLflow

**MLflow** is an **open-source platform** developed by Databricks to manage machine learning experiments.

It helps with:

- Tracking experiments
- Logging parameters
- Logging metrics
- Saving models
- Managing model versions

### Why MLflow is useful

It automatically tracks:

- Model parameters
- Code versions
- Evaluation metrics
- Model artifacts

This makes experiments **easy to reproduce and compare**.

---

# 3. Example of Using MLflow

Here is a simple example of using MLflow with a **Random Forest classifier**.

```python id="7s0q4k"
import mlflow
import mlflow.sklearn
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score
```
Start an experiment run:
```aiignore
with mlflow.start_run():

    model = RandomForestClassifier(n_estimators=100)
    model.fit(X_train, y_train)

    predictions = model.predict(X_test)
    accuracy = accuracy_score(y_test, predictions)

    mlflow.log_param("n_estimators", 100)
    mlflow.log_metric("accuracy", accuracy)

    mlflow.sklearn.log_model(model, "random_forest_model")
```

MLflow will automatically record:

Parameters

Accuracy

Model information

You can view everything in the MLflow UI dashboard

# 4. Tracking Code Versions

Another important part of reproducibility is tracking the code version used in experiments.

Sometimes results change because:

Code was updated

Bugs were fixed

Features were modified

MLflow allows you to log and track code versions, which helps you know:

Which code produced which results

Which changes improved performance

Which version introduced errors

This makes debugging and experiment comparison easier.

# 5. Model Registries

A Model Registry is a central place where trained models are stored.

It keeps track of:

Model versions

Performance metrics

Training environments

Deployment status

Example:
Model Name: Spam Classifier

Version 1
Accuracy: 85%

Version 2
Accuracy: 91%

Version 3
Accuracy: 92%

This allows teams to:

Compare models

Track improvements

Deploy the best model

MLflow provides a built-in model registry system.

# 6. Ensuring Experiment Reproducibility

To make ML experiments reproducible, you must track:

Input data

Code

Hyperparameters

Metrics

Environment settings

Example: 
Dataset: Customer Churn Dataset
Model: RandomForest
Hyperparameters: n_estimators = 100
Random Seed: 42
Accuracy: 0.89
If someone runs the same experiment with these settings, they should get the same results.

# 7. Importance of Documentation

Good documentation is essential for reproducible experiments.

Documentation should include:

Dataset details

Code used

Model parameters

Experiment results

Training environment

Example Documentation

Dataset: House Prices Dataset
Model: XGBoost
Hyperparameters:
max_depth = 6
learning_rate = 0.1
n_estimators = 200

Accuracy: 91%
Random Seed: 42
Clear documentation ensures that others can verify and improve your work.


# NOTE: This part is from Feature Engineering Course.

## Example Feature Engineering Pipeline

In real ML systems, feature engineering steps are combined into a pipeline.

Example pipeline steps:

Aggregate data

Construct new features

Transform features (scaling)

Select important features

Example pipeline structure:

```Raw Data
   ↓
Data Aggregation
   ↓
Feature Construction
   ↓
Feature Transformation
   ↓
Feature Selection
   ↓
Final Dataset for ML Model
```

## Aggregating Data from Multiple Sources

Sometimes data is stored in **different datasets**.  
Feature engineering often combines these datasets into **one dataset**.

This process is called **data aggregation**.

### Example

Suppose you are building a **customer purchase prediction model**.

Data may come from multiple sources:

1. Customer dataset
2. Purchase history dataset
3. Website activity dataset

Example files:

```text
customers.csv
purchases.csv
website_activity.csv
```
This datasets combined into one dataset.

```aiignore
import pandas as pd

customers = pd.read_csv("customers.csv")
purchases = pd.read_csv("purchases.csv")
activity = pd.read_csv("website_activity.csv")

combined_data = pd.concat([customers, purchases, activity])
```