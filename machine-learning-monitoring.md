# Monitoring Machine Learning Models

After deploying a machine learning model, the work is **not done**. Monitoring ensures the model continues to perform well in production.

---

## 1. Why Monitoring Matters
- In production, models make predictions on **new, unseen data**  
- Monitoring helps detect if the model is **working correctly** and if performance **degrades over time**  

> **Example:** A churn prediction model predicts which customers may leave. Monitoring ensures these predictions stay accurate as customer behavior changes.

---

## 2. Types of Monitoring

### a. Statistical Monitoring
- Focuses on the **input data** and **model predictions**  
- Ensures predictions are reasonable and data quality is good  

> **Example:** Checking if the predicted probability of customer churn is within expected ranges.

### b. Computational Monitoring
- Focuses on **technical performance**  
- Monitors resources like server usage, network traffic, and number of requests  

> **Example:** Ensuring the model’s server isn’t overloaded and responses are delivered on time.

> **Analogy:**  
> - Statistical = monitoring **the food quality** in a kitchen  
> - Computational = monitoring **the kitchen appliances and staff**  

---

## 3. Feedback Loop
- Over time, compare model predictions to **actual results** (ground truth)  
- Helps identify when and why the model made mistakes  
- Enables **retraining** or **improvement** of the model  

> **Example:** If the model predicts a customer will churn but they actually stay, this info is fed back to improve future predictions.

---

## 4. Best Practices
- Monitor **both statistical and computational metrics**  
- Detect problems early and take corrective actions  
- Helps maintain **reliable and accurate ML models** in production