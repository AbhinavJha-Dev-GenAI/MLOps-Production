# 03. Experiment Tracking 🧪📊

When training models, you run hundreds of variations. Experiment tracking is the "Lab Notebook" that logs everything to ensure you find the best model.

## 1. What to Track? 📝

*   **Hyperparameters**: Learning rate, batch size, epochs, architecture choice.
*   **Metrics**: Accuracy, F1-score, Precision-Recall curves, Loss.
*   **Artifacts**: The trained model weights, plots, and sample predictions.
*   **Environment**: Dependencies (`requirements.txt`), Python version, and GPU specs.

---

## 2. Industry Standard Tools 🛠️

### MLflow
An open-source platform for the whole ML lifecycle.
- **Tracking**: Log parameters and metrics.
- **Registry**: Versioning and staging (Staging/Production) models.

### Weights & Biases (W&B)
A cloud-based tool famous for its superior visualizations and dashboards.
- Perfect for collaborative teams.
- Interactive loss curves and system usage (GPU/CPU) tracking.

---

## 🛠️ Essential Snippet (MLflow Tracking)

```python
import mlflow

# Start an experiment
mlflow.set_experiment("Fraud_Detection_v1")

with mlflow.start_run():
    # Log parameters
    mlflow.log_param("lr", 0.01)
    mlflow.log_param("n_estimators", 100)
    
    # ... Training Code ...
    
    # Log metrics
    mlflow.log_metric("accuracy", 0.95)
    
    # Log the model itself
    mlflow.sklearn.log_model(model, "random_forest_model")
```

---

## 🧩 The "Pro" Edge
- **System Metrics**: Tracking GPU temperature and memory can help you find bottlenecks in your training code.
- **Tags**: Use tags (e.g., `trial_type: baseline`) to quickly filter through hundreds of runs in the dashboard.
