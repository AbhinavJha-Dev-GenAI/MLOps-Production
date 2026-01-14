# 01. ML Lifecycle 📈🔄

The Machine Learning Lifecycle is a iterative process that spans from initial problem definition to a model's retirement in production.

## 1. The Core Stages 🛠️

1.  **Problem Definition**: Defining business KPIs (e.g., Click-Through Rate) and success metrics.
2.  **Data Ingestion & Cleaning**: Collecting raw data and transforming it into a usable format.
3.  **Exploratory Data Analysis (EDA)**: Understanding distributions, correlations, and outliers.
4.  **Feature Engineering**: Selecting and transforming variables to improve model performance.
5.  **Model Training & Tuning**: Running experiments with different algorithms and hyperparameters.
6.  **Offline Evaluation**: Testing on a hold-out dataset using metrics like F1-Score or RMSE.
7.  **Deployment**: Pushing the model to a production environment (API, Batch, or Edge).
8.  **Monitoring & Maintenance**: Tracking real-world performance and retraining as needed.

---

## 2. MLOps Maturity Levels (Google's Framework) ⚖️

*   **Level 0: Manual Process**: Script-driven, manual deployments, and no automated monitoring.
*   **Level 1: ML Pipeline Automation**: Automated pipeline for model training but still manual model deployment. Focus on reproducible experiments.
*   **Level 2: CI/CD Pipeline Automation**: Fully automated CI/CD and Continuous Training (CT) systems. Zero-touch deployments to production.

---

## 3. The "Hidden Technical Debt" 🕸️

> [!IMPORTANT]
> In a production ML system, **only about 5% of the code is actual ML code**. The rest (95%) is "plumbing": data collection, verification, resource management, and monitoring. This is known as "Hidden Technical Debt."

---

## 🛠️ Essential Concept: Continuous Training (CT)

Unlike standard software, ML models degrade over time due to **Data Drift**. CT allows the system to automatically trigger a new training run when performance drops, ensuring the model stays relevant without manual intervention.

---

## 📊 Summary
Understanding the lifecycle is the difference between writing "Notebook code" and building "Production systems." Every stage must be reproducible and trackable.
