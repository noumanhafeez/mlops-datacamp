# Data Quality and Ingestion in MLOps

During the **Design Phase**, a crucial step is making sure the **data is good quality** and figuring out **how to get it** into the system. High-quality data is essential because **the performance of a machine learning model depends heavily on the data**.

---

## 1. What is Data Quality?
Data quality measures how well the data serves its intended purpose. It can be evaluated across four main **dimensions**:

1. **Accuracy:** Is the data correct?  
2. **Completeness:** Are any values missing?  
3. **Consistency:** Are definitions uniform across the organization?  
4. **Timeliness:** Is the data up-to-date and available when needed?  

> **Example:** Predicting customer churn:  
> - **Accuracy:** Customer age is correct (not 18 instead of 32)  
> - **Completeness:** All customers have last names recorded  
> - **Consistency:** All departments define an “active customer” the same way  
> - **Timeliness:** Orders are synchronized in real-time, not daily  

> **Tip:** Low quality in one dimension doesn’t mean failure. You can fix it by collecting more data, cleaning data, or filling missing values from other sources.

---

## 2. Data Ingestion
Data ingestion is about **extracting and processing data** for ML models. This is often done using an **automated data pipeline**.  

A common pipeline process is **ETL** (Extract, Transform, Load):

1. **Extract:** Pull data from sources (databases, APIs, files)  
2. **Transform:** Clean, format, and structure the data for use  
3. **Load:** Save the data into a database or system for ML use  

> **Example:** A pipeline that updates daily sales data:  
> - Extract: Read sales records from the company database  
> - Transform: Convert dates to a standard format, fill missing values  
> - Load: Store cleaned data in an ML-ready database  

**Automated checks** in the pipeline ensure data quality, e.g., verifying that the temperature column contains only numbers. These checks help prevent faulty data from affecting model performance and speed up development.

---

**Key Idea:** High-quality data + efficient data ingestion = smoother model development and more reliable predictions.