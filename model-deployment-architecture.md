# Machine Learning Deployment Architecture

After preparing and containerizing an ML model, the next step is **deciding how to deploy it in a scalable and reliable way**. This involves choosing the right **architecture** and setting up communication between services.

---

## 1. Monolithic vs. Microservices Architecture
- **Monolithic architecture:** All services are bundled into **one large application**.  
  - **Problem:** If one part fails, the **whole application fails**.  
  - Scaling is harder because all parts are interconnected.  

- **Microservices architecture:** The application is split into **independent smaller services**.  
  - Each service can be **deployed, updated, and scaled separately**.  
  - **Failure of one service** doesn’t affect the others.  
  - Good for complex applications but can be **costly for very small apps** because each service needs compute resources and maintenance.  

> **Example:** A webshop with separate services for:  
> - Payments  
> - Shopping cart  
> - Inventory  
>  
> Using microservices, if the payment service fails, the inventory and cart still work.

---

## 2. Deploying ML Models as Microservices
- ML models are commonly deployed as **microservices**  
- This allows the model to make predictions on **new, unseen data** (a process called **inferencing**)  

> **Example:** Sending a customer’s data to a churn prediction model, which returns the probability of that customer leaving.

---

## 3. Application Programming Interface (API)
- Microservices communicate using an **API** (Application Programming Interface)  
- An API defines **pre-set input and output rules**, allowing services to interact correctly  

> **Analogy:** An API is like a **restaurant menu**:  
> - You order “Pizza Carciofo” from the menu (input)  
> - The kitchen (service/model) prepares it  
> - The waiter delivers it to you (output)  
>  
> Without the menu (API), communication between customer and kitchen (services) would fail.

---

**Key Idea:** Using **microservices and APIs** ensures ML models are **scalable, reliable, and able to communicate effectively** with other parts of the application, allowing seamless deployment in production.