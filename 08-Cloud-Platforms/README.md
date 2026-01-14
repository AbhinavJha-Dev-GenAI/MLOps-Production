# 08. Cloud ML Platforms (AWS, GCP, Azure) ☁️🔬

Building a custom MLOps infra is hard. Cloud providers offer "Integrated" platforms that handle everything from labeling to deployment.

## 1. AWS SageMaker 🟠

The most mature and feature-rich platform.
*   **Ground Truth**: Data labeling service.
*   **Feature Store**: Repository for sharing ML features.
*   **Model Monitor**: Automatic drift detection.
*   **Canvas**: No-code ML for business analysts.

---

## 2. Google Vertex AI 🟢

Known for its seamless integration with the rest of Google Cloud (BigQuery, GCS).
*   **Vertex Pipelines**: Managed Kubeflow for orchestrating workflows.
*   **Model Garden**: A repository of pre-trained models (including Gemini/Imagen).
*   **AutoML**: Let Google find the best architecture for you.

---

## 3. Azure Machine Learning 🔵

The enterprise-favorite, offering deep integration with Microsoft 365 and high security.
*   **Designer**: Drag-and-drop interface for building pipelines.
*   **Managed Endpoints**: Simplified scaling and model deployment.
*   **Responsible AI Dashboard**: Tools for checking bias and fairness.

---

## 🛠️ Essential Comparison

| Feature | AWS SageMaker | Google Vertex AI | Azure ML |
| :--- | :--- | :--- | :--- |
| **Best For** | Power users / Complex Infra | Tech-focused / BigQuery users | Enterprise / Secure systems |
| **Easiness** | Moderate | High | High |
| **Pricing** | Granular / Pay-per-use | Tiered / Integrated | Enterprise licenses |

---

## 🧩 Pro-Tip: Multi-Cloud vs. Cloud-Native
While cloud-native tools are easy, they can lead to **Vendor Lock-in**. Many teams use **Open Source** tools (like MLflow and K8s) on cloud-managed clusters to stay flexible.
