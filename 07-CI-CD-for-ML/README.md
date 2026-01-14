# 07. CI/CD & CT for Machine Learning 🏗️⚙️

Automation is what separates "ML" from "MLOps."

## 1. CI (Continuous Integration) 🧪

In MLOps, CI is for both **Code** and **Data**.
*   **Code Tests**: Standard unit and integration tests.
*   **Data Validation**: Checking if new data matches the expected schema and has reasonable distributions.
*   **Model Testing**: Running the model on a small, fast "smoke test" dataset to ensure it doesn't crash.

---

## 2. CD (Continuous Deployment) 🚀

Automatically pushing validated models to production.
*   **Blue-Green Deployment**: Having two identical environments (one for old, one for new) and switching traffic instantly.
*   **Canary Deployment**: Slowly rolling out the new model to 5%, then 20%, then 100% of users to monitor for early failures.

---

## 3. CT (Continuous Training) 🔄

The unique part of MLOps.
- **Trigger**: Performance drop (Drift) or scheduled (e.g., every Monday).
- **Process**: Pull new data -> Validate -> Retrain on GPU cluster -> Evaluate -> If better than production model, trigger CD.

---

## 🛠️ Essential Snippet (GitHub Actions for ML)

```yaml
name: ML CI/CD
on: [push]

jobs:
  test_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v2
        
      - name: Build Docker Image
        run: docker build -t my-model:latest .
        
      - name: Run Schema Tests
        run: python src/tests/test_data_schema.py
        
      - name: Run Model Unit Test
        run: python src/tests/test_inference.py
```

---

## 🌍 Summary
Automation reduces manual errors and ensures that the model in production is always the best possible version trained on the most relevant data.
