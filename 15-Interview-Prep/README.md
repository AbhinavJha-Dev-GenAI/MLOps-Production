# 15. MLOps Interview Preparation 🧠🧱

Technical, infrastructure, and design questions for MLOps/MLE roles.

## 1. Lifecycle & Process 📖

*   **Q: What is the difference between Data Drift and Concept Drift?**
    - *A:* Data Drift is a change in the inputs ($x$), while Concept Drift is a change in the mapping from input to output ($y|x$).
*   **Q: Why use DVC over Git LFS?**
    - *A:* DVC is platform-agnostic (works with S3, GCS, etc.), handles data lineage, and doesn't bloat the Git server.
*   **Q: Explain MLOps Level 1 vs. Level 2.**
    - *A:* Level 1 automates training (Pipelines). Level 2 automates both training and deployment (Full CI/CD/CT).

---

## 2. Infrastructure & Scaling 🏗️

*   **Q: When would you use a Feature Store?**
    - *A:* When multiple models use the same features, or when you need to ensure zero skew between training and real-time inference.
*   **Q: How do you handle a model that is too large for a single GPU?**
    - *A:* Use **Model Parallelism** or **Quantization** (FP32 to INT8) to reduce the memory footprint.
*   **Q: Explain "Shadow Deployment."**
    - *A:* Running a new model in production to receive real data without using its outputs, purely for comparison with the live model.

---

## 3. Engineering Scenarios 🧪

*   **Scenario: Your model's accuracy dropped by 5% over the weekend. What do you check first?**
    - *A:* First, check for **Data Pipeline failures** (missing data, nulls). Second, use Evidence AI to check for **Data Drift**. Third, look at upstream changes in feature engineering code.
*   **Scenario: You have 100 models to deploy. How do you manage them?**
    - *A:* Use a **Model Registry** (like MLflow) for versioning and a **Container Orchestrator** (Kubernetes) for scaling and management.

---

## 🎯 MLOps Engineering Cheat Sheet
1. **Best for Tracking**: MLflow / W&B.
2. **Best for Orchestration**: Kubernetes / Kubeflow.
3. **Best for Data Versioning**: DVC.
4. **Best for Quick APIs**: FastAPI.
