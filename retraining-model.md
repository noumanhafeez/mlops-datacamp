# Retraining Machine Learning Models

After deploying a model, retraining is an important step to keep it accurate over time.

---

## 1. Why Retraining is Needed
- Data **changes over time**, and models trained on old data may become less accurate  
- Retraining uses **new data** to create an updated model that adapts to new patterns  

> **Example:** A churn prediction model may need retraining when new types of customers join or customer behavior changes.

---

## 2. Types of Drift

### a. Data Drift
- Changes in the **input data** over time  
- Example: New customers are from a different age group or region  
- May affect performance, but not always  

### b. Concept Drift
- Changes in the **relationship between input and target**  
- Example: Previously, customers with high complaints would churn; now they stay loyal  
- Can significantly **reduce model accuracy**  

---

## 3. How Often to Retrain
Depends on several factors:
1. **Business environment:** Fast-changing markets need more frequent retraining  
2. **Cost of retraining:** Complex models require more resources and money  
3. **Business requirements:** If high accuracy is required, retraining must happen sooner when accuracy drops  

> **Term:** The speed at which model accuracy decreases is called **model degradation**.

---

## 4. Retraining Methods

### a. Use Only New Data
- Train a **separate model** on new data  
- Old model stays as is

### b. Combine Old and New Data
- Train a **single updated model** using both old and new data  
- Decision depends on **domain, cost, and required performance**

---

## 5. Automatic Retraining
- Advanced setups can trigger **automatic retraining** when:
  - Enough new data is available  
  - Concept drift is detected  

> **Example:** Automatically retraining when the average age of customers shifts significantly.

---

**Key Idea:** Retraining ensures your ML models **stay accurate and relevant** as data and patterns evolve.