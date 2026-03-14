# CI/CD and Deployment Strategies in MLOps

After preparing a machine learning model for production, **CI/CD and deployment strategies** help ensure models are released **reliably, safely, and efficiently**.

---

## 1. CI/CD Pipeline
- **CI/CD** stands for **Continuous Integration / Continuous Deployment**  
- It automates **testing and deployment** of ML models, ensuring changes are **frequent, reliable, and reproducible**  

> **Analogy:** Like testing a new recipe in a restaurant:  
> - CI = Test the recipe before putting it on the menu  
> - CD = Automatically launch the recipe for guests once it passes testing

---

## 2. Continuous Integration (CI)
- Automatically integrates **code changes** into the main project  
- Runs **automatic tests** on each change to catch errors early  

> **Example:** Updating a model’s preprocessing code triggers automated tests to ensure predictions remain correct.

---

## 3. Continuous Deployment (CD)
- Automates the **release of validated changes** to production  
- Works hand-in-hand with CI, so **tested changes go live automatically**  

> **Example:** Once a new feature in a churn prediction model is tested, it’s automatically deployed to the production environment.

---

## 4. Deployment Strategies
Different ways to deploy new ML models while managing **risk** and **resources**:

### a. Basic Deployment
- **Old model is fully replaced** by the new model  
- All incoming data is sent to the new model  
- **Pros:** Easy to implement, uses few resources  
- **Cons:** High risk if the new model fails  

> **Example:** Replacing the old spam filter with a new one for all incoming emails at once.

### b. Shadow Deployment
- New model receives **same input as old model**, but only the old model’s predictions are used in production  
- Compare outputs of both models to test performance  
- **Pros:** No risk to users  
- **Cons:** Higher resource usage, since both models run  

> **Example:** Test a new recommendation model in parallel with the old one without affecting what users see.

### c. Canary Deployment
- New model is used for a **small fraction of incoming data**  
- Monitors performance before rolling out fully  
- **Pros:** Lower resource usage than shadow deployment, safer than basic deployment  
- **Cons:** Slightly higher risk than shadow deployment if the new model fails  

> **Example:** Launch a new fraud detection model to 5% of transactions first, then gradually increase if it performs well.

---

**Key Idea:** Using **CI/CD pipelines and deployment strategies** ensures ML models are **released safely, tested in real conditions, and can be rolled back or monitored**, balancing **risk, resources, and reliability**.