# 13. MLOps Projects 🛠️🏗️

Hands-on project ideas to turn theoretical knowledge into a production-grade portfolio.

## Project 1: End-to-End Sentiment API with CI/CD 📈
*   **Goal**: Create a service that classifies text sentiment and automatically redeploys a new model when code is pushed to GitHub.
*   **Tech Stack**: FastAPI, GitHub Actions, Docker, MLflow.
*   **Key Learning**: Automated testing for ML and continuous integration.

## Project 2: Real-time Fraud Detection on Kubernetes 🛡️
*   **Goal**: Deploy a high-throughput fraud detection model on a K8s cluster that autoscales based on traffic.
*   **Tech Stack**: Kubernetes (Minikube/EKS), Prometheus, Grafana, BentoML.
*   **Key Learning**: Orchestration, resource monitoring, and autoscaling.

## Project 3: Drift Detection Pipeline 📉
*   **Goal**: A system that monitors an incoming data stream and alerts a Slack channel when the feature distribution shifts significantly.
*   **Tech Stack**: Evidently AI, Great Expectations, AWS Lambda (or any serverless function).
*   **Key Learning**: Silent failure detection and real-world monitoring.

## Project 4: Model Optimization Hub ⚡
*   **Goal**: A tool that takes a large PyTorch model and outputs multiple optimized versions (ONNX, Quantized INT8, TensorRT).
*   **Tech Stack**: PyTorch, ONNX Runtime, TensorRT.
*   **Key Learning**: Inference speedups and hardware-specific compilation.

---

## 🚀 Getting Started
1.  **Start Small**: Build the "Project 1" (API + Docker) first. Infrastructure is the hardest part.
2.  **Use Free Tiers**: Use **GitHub Actions** (free for public repos) and **Weights & Biases** (free for individuals) to keep costs zero.
3.  **Document everything**: Employers care more about *how* you solved the infrastructure challenges than the final model's accuracy.
