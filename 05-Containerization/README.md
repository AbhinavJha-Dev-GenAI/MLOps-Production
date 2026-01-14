# 05. Containerization (Docker & K8s) 🐳🏗️

Containerization ensures that your ML application runs exactly the same way in production as it did on your laptop, eliminating the "it works on my machine" problem.

## 1. Why Docker for ML? 📦

ML libraries (like PyTorch or TensorFlow) have complex dependencies, specific CUDA versions, and OS-level requirements.
*   **Isolation**: Each model runs in its own "container" with its own specific environment.
*   **Portability**: Move a container from a local workstation to AWS or GCP without modifications.
*   **Reproducibility**: The Dockerfile captures every installation step perfectly.

---

## 2. Orchestration with Kubernetes (K8s) ☸️

Kubernetes is the "manager" of containers. For large ML systems:
- **Scalability**: If traffic increases, K8s automatically spins up more containers.
- **Self-healing**: If a container crashes, K8s restarts it automatically.
- **Resource Management**: Properly distributes GPU/CPU resources among different models.

---

## 3. Kubeflow: ML Context on K8s 🧠

Kubeflow is an open-source platform built on top of K8s specifically for ML.
- **Pipelines**: Creating multi-step workflows (Preprocessing -> Training -> Deployment).
- **Katib**: Automated hyperparameter tuning within the cluster.

---

## 🛠️ Essential Snippet (ML Dockerfile)

```dockerfile
# Use a lightweight PyTorch base image
FROM pytorch/pytorch:2.1.0-cuda11.8-cudnn8-runtime

# Set working directory
WORKDIR /app

# Copy dependencies and install
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the model and API code
COPY ./src /app/src
COPY ./model.pkl /app/model.pkl

# Expose the port for FastAPI
EXPOSE 8000

# Start the application
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

## 🌍 Summary
Docker is the "packaging," and Kubernetes is the "delivery truck." Together, they form the backbone of modern, scalable ML infrastructure.
