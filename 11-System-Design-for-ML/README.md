# 11. System Design for Machine Learning 🏗️🧩

Designing a high-scale ML system is different from standard software engineering. It requires thinking about data flow, latency, and consistency.

## 1. Feature Stores: The Source of Truth 🗃️

In large teams, different people use the same features. A feature store (e.g., **Feast**, **Tecton**) provides:
*   **Consistency**: Ensures training and inference use the *exact* same feature logic.
*   **Reusability**: One person defines "User_Avg_Purchase," and the whole team can use it.
*   **Offline/Online Sync**: Automatically moves data from Data Warehouses (Offline) to low-latency Key-Value stores like Redis (Online).

---

## 2. Distributed Training Paradigms 🌍

When a model is too big for one GPU:
*   **Data Parallelism**: The model is copied to every GPU, and each GPU processes a different slice of data. Gradients are averaged at the end.
*   **Model Parallelism**: The model itself is split across multiple GPUs (e.g., Layer 1-10 on GPU 1, Layer 11-20 on GPU 2).

---

## 3. Serving Architectures 🏛️

*   **Embedded Model**: The model is baked into the app code (lowest latency, hardest to update).
*   **Model as a Service (MaaS)**: The app calls an external API. Scalable and easy to update, but adds network latency.
*   **Client-Side Serving**: Model runs in the browser (TensorFlow.js) or on the mobile device (CoreML/TFLite). Zero server costs and high privacy.

---

## 🛠️ Essential Snippet (Conceptual Feature Store call)

```python
# Instead of recalculating features manually...
features = feature_store.get_online_features(
    feature_view="user_purchase_behavior",
    entity_id={"user_id": 12345}
).to_dict()

# ...you get consistent, ready-to-use features instantly
prediction = model.predict(features)
```

---

## 🧩 The "Pro" Edge
When designing, always ask: **"What happens if the model is down?"** Always have a heuristic fallback (e.g., show "Global Top 10" if the personalized recommendation model fails) to ensure the system doesn't crash.
