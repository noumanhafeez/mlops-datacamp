# Feature Engineering in MLOps

After the **Design Phase**, the next step in machine learning development is **Feature Engineering**. This step focuses on **creating the most informative variables (features) from raw data** to improve model performance.

---

## 1. What is Feature Engineering?
Feature engineering is the process of:

- Selecting, transforming, and creating features from raw data  
- Using features directly from data or **engineering new features** to make the model more effective  

> **Example:**  
> Customer dataset with:  
> - `Number of Orders`  
> - `Total Expenditure`  
>  
> New feature: `Average Expenditure per Order = Total Expenditure / Number of Orders`  

---

## 2. Goal of Feature Engineering
- Enhance **model performance** by focusing on the **most relevant features**  
- Avoid adding irrelevant or redundant features  
- Use tools like **feature selection, feature stores, and data version control** to automate and manage features  

---

## 3. Feature Selection
- Use **domain knowledge** to choose meaningful features  
- Check **correlations** to remove redundant features  
- Evaluate **feature importance** to see which features influence the model most  
- Advanced techniques:  
  - Univariate Selection  
  - Principal Component Analysis (PCA)  
  - Recursive Feature Elimination (RFE)  

> **Example:** In a churn prediction model, you may select features like `Number of Complaints` and `Monthly Usage`, but drop `Customer ID` since it doesn’t affect predictions.

---

## 4. Feature Store
- A **central repository** for features  
- Helps **reuse and maintain consistency** across projects  
- Useful for **large teams or multiple projects**, but optional for smaller, simpler projects  

> **Example:** Multiple ML models predicting customer behavior can share features like `Average Expenditure` from a feature store, avoiding duplicate work.

---

## 5. Data Version Control (DVC)
- Tracks **changes in datasets**, similar to Git for code  
- Helps **maintain consistency** and allows rolling back to earlier dataset versions  

> **Example:** If a dataset is updated with new customer orders, DVC allows you to revert to the previous version if the new data causes issues.

---

**Key Idea:** Feature engineering ensures your ML model uses **meaningful, high-quality inputs** to make better predictions while keeping the process **organized and reproducible**.