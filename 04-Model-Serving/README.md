# 04. Model Serving 🚀🍽️

Model serving is the process of making your trained model available for predictions in a production environment.

## 1. Serving Paradigms 🏗️

*   **Real-time (Request-Response)**: Low latency, one prediction at a time (e.g., Fraud check on credit card swipe).
*   **Batch Inference**: Processing large amounts of data at once (e.g., Generating personalized recommendations for all users every night).
*   **Streaming Inference**: Processing a continuous flow of data as it arrives (e.g., Sentiment analysis on live Twitter feed).

---

## 2. Serving Frameworks 🧪

### FastAPI (Lightweight & Modern)
The go-to choice for building Python-based ML APIs.
- Very fast performance.
- Automatic Swagger (OpenAPI) documentation.

### Dedicated Model Servers
For high-throughput, enterprise-scale production:
*   **TensorFlow Serving**: Highly optimized for TF/Keras models.
*   **TorchServe**: Co-developed by AWS and Meta for PyTorch models.
*   **BentoML**: A "unified" framework that simplifies packaging models into containers.

---

## 3. Inference Optimizations ⚡

To reduce latency and cost in production:
*   **Batching**: Grouping multiple incoming requests into a single GPU computation.
*   **Model Quantization**: Using 8-bit integers instead of 32-bit floats.
*   **Pruning**: Removing non-essential weights from the model.

---

## 🛠️ Essential Snippet (Simple FastAPI Server)

```python
from fastapi import FastAPI
import joblib

app = FastAPI()
model = joblib.load("model.pkl")

@app.post("/predict")
def predict(data: dict):
    # Extract features from incoming JSON
    features = [data['val1'], data['val2']]
    prediction = model.predict([features])
    return {"prediction": int(prediction[0])}

# Run with: uvicorn main:app --reload
```

---

## 📊 Summary
Model serving isn't just about `model.predict()`. It's about handling concurrency, logging requests, and ensuring the API is secure and fast enough for the end user.
