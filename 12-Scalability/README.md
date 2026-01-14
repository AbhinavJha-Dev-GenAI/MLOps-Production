# 12. Scalability in MLOps 📈🚀

How do you handle 10,000 requests per second across millions of users?

## 1. Load Balancing & Replication ⚖️

*   **Horizontal Scaling**: Instead of one big GPU, use 10 smaller GPUs. Kubernetes (K8s) handles the routing of traffic between these "replicas."
*   **Model Replicas**: Keeping multiple instances of the same model running to handle parallel requests.

---

## 2. Dealing with GPU Bottlenecks 🔌

GPUs are expensive and can only process a finite number of math operations at once.
*   **Batching at Inference**: Collecting 32 requests and processing them in one "GPU hit." This significantly increases throughput but might slightly increase individual latency.
*   **GPU Sharing**: Using technologies like NVIDIA **MPS** (Multi-Process Service) to run multiple small models on a single large GPU.

---

## 3. Asynchronous Processing ⏳

Not every prediction needs to be instant.
*   **Message Queues (Kafka/RabbitMQ)**: For tasks that can take a few seconds (e.g., generating a summary of a 100-page PDF). The user gets a "Job ID" and polls for the result later.

---

## 🛠️ Essential Snippet (Conceptual Async Queue)

```python
# 1. User submits a job
job_id = celery_app.send_task("process_complex_image", args=[image_data])

# 2. Worker (on a different machine) picks it up
@app.task
def process_complex_image(data):
    # Heavy GPU computation here
    result = model.predict(data)
    save_to_db(result)
```

---

## 🧩 Practical Tip
**Autoscaling**: Use Kubernetes **HPA** (Horizontal Pod Autoscaler) to automatically increase the number of model replicas when the CPU/GPU usage hits 70%, and scale back down at night to save money.
