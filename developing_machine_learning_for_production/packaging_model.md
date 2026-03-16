# Packaging Machine Learning Models

## Introduction

After training a machine learning model, we cannot directly use it in real-world applications.  
We must **package the model** so it can be deployed and run in different environments.

**Packaging** means preparing the model along with its required files, libraries, and environment so it can run reliably anywhere.

Example:

If you train a model on your laptop but deploy it on a server, the model should still work correctly. Packaging ensures this.

---

# Why Packaging ML Models Matters

Packaging helps make ML models:

- **Portable** – Can run on different machines
- **Reproducible** – Same results in different environments
- **Easy to deploy** – Simple to move to production
- **Compatible** – Works with required libraries and dependencies

There are three common ways to package ML models:

1. **Serialization**
2. **Environment Packaging**
3. **Containerization**

---

# 1. Serialization

## What is Serialization?

Serialization is the process of **saving a trained model to a file** so it can be loaded later.

Instead of training the model every time, we just **load the saved model and use it for predictions**.

### Example

Train a model once:

```
Train Model → Save Model → Load Model → Make Predictions
```

---

## Serializing Scikit-Learn Models

In Python, we often use **pickle** to save models.

### Example

```python
import pickle
from sklearn.ensemble import RandomForestClassifier

# Train model
model = RandomForestClassifier()
model.fit(X_train, y_train)

# Save model
with open("model.pkl", "wb") as f:
    pickle.dump(model, f)

# Load model
with open("model.pkl", "rb") as f:
    loaded_model = pickle.load(f)

prediction = loaded_model.predict(X_test)
```

Now the model can be reused without retraining.

---

# Serializing Deep Learning Models

Deep learning frameworks also support serialization.

## PyTorch Example

```python
import torch

# Save model
torch.save(model.state_dict(), "model.pth")

# Load model
model.load_state_dict(torch.load("model.pth"))
```

---

## TensorFlow Example

TensorFlow uses **SavedModel format**.

```python
model.save("model_directory")
```

This format is optimized for production deployment.

---

# 2. Environment Packaging

Machine learning models depend on many libraries such as:

- numpy
- pandas
- scikit-learn
- tensorflow
- pytorch

If the correct versions are not installed, the model might fail.

Environment packaging ensures **the same environment is recreated anywhere**.

---

## Virtual Environments

Tools used:

- **virtualenv**
- **conda**

Example:

```
project/
│
├── model.pkl
├── requirements.txt
├── run_model.py
```

Example `requirements.txt`:

```
numpy==1.24
pandas==2.0
scikit-learn==1.3
```

Then install dependencies:

```
pip install -r requirements.txt
```

---

# 3. Containerization

Containerization packages **everything together**:

- Model
- Code
- Dependencies
- Environment

This is done using **Docker**.

Docker creates a **container**, which is a portable environment that runs the same everywhere.

Example:

```
Laptop → Cloud Server → Production System
```

The model will behave exactly the same.

---

# Example Dockerfile

A **Dockerfile** defines how to build a container.

Example:

```dockerfile
FROM python:3.8

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "run_model.py"]
```

---

## Build Docker Image

```
docker build -t ml-model .
```

## Run Docker Container

```
docker run ml-model
```

Now the model runs inside a container.

---

# Experiment → Docker Workflow

A typical ML workflow looks like this:

### Step 1 — Train Model

Train model using data.

```
train_model.py
```

---

### Step 2 — Serialize Model

Save trained model to a file.

```
model.pkl
```

---

### Step 3 — Package Dependencies

Create:

```
requirements.txt
```

---

### Step 4 — Containerize with Docker

Create Docker image containing:

- model
- code
- dependencies
- runtime environment

---

### Step 5 — Deploy

Run the Docker container on:

- cloud servers
- production systems
- APIs

---

# Real World Example

Imagine you built a **house price prediction model**.

### Training Phase

```
Train model → RandomForest
```

---

### Save Model

```
house_price_model.pkl
```

---

### Package Environment

```
requirements.txt
```

---

### Create Docker Container

The container contains:

- model
- prediction script
- Python
- libraries

---

### Deploy

The model is deployed on a cloud server and used by a **web application**.

Users enter house details → model predicts price.

---

# Key Takeaways

- **Packaging** prepares ML models for deployment.
- **Serialization** saves trained models to files.
- **Environment packaging** ensures required libraries are installed.
- **Containerization** packages everything using Docker.
- Docker ensures the model runs **consistently across different systems**.

---

# Final Summary

Packaging ML models is a critical step before deployment. It ensures models are portable, reproducible, and easy to run in different environments. Common methods include serialization for saving models, environment packaging for managing dependencies, and containerization using Docker for creating fully portable ML applications.