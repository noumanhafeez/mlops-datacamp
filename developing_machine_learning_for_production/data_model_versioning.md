# Data and Model Versioning in MLOps

## Introduction

In machine learning projects, experiments are performed many times using different datasets, features, and models.  
To keep track of these changes, we use **versioning**.

**Versioning** means assigning a version number to datasets, features, and models so we can track changes over time.

### Why Versioning is Important

Versioning helps us:

- Reproduce previous experiments
- Track what changed in each experiment
- Compare different versions of models and data
- Roll back to an older working version if something breaks

For example, if a new model performs worse than the previous one, we can easily go back to the older version.

---

# Major and Minor Versioning

Version numbers usually follow this format:

```
Major.Minor
```

Example:

```
1.0
1.1
1.2
2.0
```

## Major Version

A **major version** indicates a **big change**.

Examples of major changes:

- New dataset added
- New machine learning algorithm
- Large change in feature engineering

Example:

```
Model 1.0 → Random Forest
Model 2.0 → XGBoost
```

Since the algorithm changed, it becomes a **major update**.

---

## Minor Version

A **minor version** indicates a **small change**.

Examples of minor changes:

- Hyperparameter tuning
- Feature scaling
- Small bug fixes

Example:

```
Model 1.0 → Random Forest
Model 1.1 → Random Forest with tuned hyperparameters
```

The algorithm is still the same, so it is a **minor update**.

---

# Versioning Training Data

Datasets also change over time, so we need to version them.

We can label dataset versions like:

```
Data v1.0
Data v1.1
Data v1.2
Data v2.0
```

### Example

| Data Version | Change |
|---------------|--------|
| 1.0 | Initial dataset |
| 1.1 | Added feature scaling |
| 1.2 | Added feature selection (Chi-Square) |
| 2.0 | Added completely new data source |

This allows us to know **which dataset was used for which experiment**.

---

# Feature Stores

A **Feature Store** is a centralized system that stores and manages features used in machine learning models.

## Why Feature Stores Are Useful

Feature stores help:

- Store feature versions
- Share features between teams
- Avoid duplicate work
- Maintain consistency across experiments

### Example

Instead of every ML engineer creating the same features again, they can reuse them from the **feature store**.

Popular feature store tools include:

- Feast
- Tecton
- AWS SageMaker Feature Store

---

# Versioning ML Models

Just like datasets, ML models also need versioning.

Each trained model gets a version number.

Example:

| Model Version | Data Version | Model Type |
|---------------|-------------|-----------|
| 1.0 | Data 1.0 | Random Forest |
| 1.1 | Data 1.1 | Random Forest (tuned) |
| 2.0 | Data 1.2 | XGBoost |

Explanation:

1. Model **1.0** → First model trained using dataset 1.0.
2. Model **1.1** → Same algorithm but hyperparameters changed.
3. Model **2.0** → Algorithm changed from Random Forest to XGBoost (major change).

---

# Model Stores

A **Model Store** is a repository where trained models are stored and managed.

It helps us:

- Track different model versions
- Deploy models
- Roll back to older models if needed

Example tools:

- MLflow Model Registry
- AWS SageMaker Model Registry
- Kubeflow Model Registry

---

# Example: Model Versioning with MLflow

**MLflow** is a popular tool used in MLOps for tracking experiments and versioning models.

Example:

```python
import mlflow

mlflow.set_experiment("Model Versioning")

with mlflow.start_run():
    
    model_version = "1.0"
    
    mlflow.log_param("model_version", model_version)
    
    mlflow.sklearn.log_model(model, "model")
```

This logs the model version and stores the trained model in MLflow.

---

# Simple Real-World Example

Imagine you are building a **house price prediction model**.

### Step 1

```
Data v1.0
Model v1.0
Algorithm: Random Forest
```

---

### Step 2

You add feature scaling.

```
Data v1.1
Model v1.1
Algorithm: Random Forest
```

---

### Step 3

You switch to a better algorithm.

```
Data v1.2
Model v2.0
Algorithm: XGBoost
```

---

### Step 4

You add a completely new dataset.

```
Data v2.0
Model v2.1
Algorithm: XGBoost
```

Now you can clearly see **how your ML system evolved**.

---

# Key Takeaways

- **Versioning** tracks changes in datasets and models.
- **Major version** = big change (new model or new dataset).
- **Minor version** = small change (hyperparameters or features).
- **Feature stores** manage and share feature versions.
- **Model stores** manage and track trained models.
- Tools like **MLflow** help automate version tracking.

---

# Final Summary

Data and model versioning are essential in MLOps to ensure reproducibility, traceability, and collaboration. By assigning version numbers to datasets and models, ML engineers can easily track experiments, compare results, and revert to previous versions if necessary.

Without versioning, managing machine learning experiments becomes very difficult as projects grow larger and more complex.