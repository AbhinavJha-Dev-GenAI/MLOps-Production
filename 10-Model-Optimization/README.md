# 10. Model Optimization ⚡💎

Modern ML models (especially LLMs) are huge. Model optimization is the art of making them smaller and faster without losing too much performance.

## 1. Core Techniques 🛠️

### Quantization
Reducing the precision of the model's numbers.
- **FP32** (32-bit float) -> **FP16** (16-bit float) or **INT8** (8-bit integer).
- **Result**: Drastically reduces memory usage and speeds up GPU/CPU inference.

### Pruning
Removing non-essential connections (weights) that stay close to zero throughout training.
- **Structured Pruning**: Removing entire neurons or layers.
- **Unstructured Pruning**: Removing individual weights (leads to "sparse" matrices).

### Knowledge Distillation
Training a small "Student" model to mimic the outputs of a large, high-performing "Teacher" model.
- *Example:* DistilBERT is a smaller, faster version of BERT that retains 95% of its performance.

---

## 2. Specialized Runtimes & Compilers ⚙️

Generic Python inference is slow. Use these for production:
*   **ONNX (Open Neural Network Exchange)**: A common format that allows you to train in one framework (PyTorch) and run in any other highly optimized environment.
*   **TensorRT (NVIDIA)**: A compiler that optimizes models specifically for NVIDIA hardware.
*   **OpenVINO (Intel)**: Optimization specifically for Intel CPUs and integrated GPUs.

---

## 🛠️ Essential Snippet (Simple Quantization with PyTorch)

```python
import torch

# Load floating-point model
model_fp32 = MyModel()

# Convert to 8-bit integer quantization
model_int8 = torch.quantization.quantize_dynamic(
    model_fp32,  # original model
    {torch.nn.Linear},  # layers to quantize
    dtype=torch.qint8
)

# Observe the size difference
print(f"FP32 size: {os.path.getsize('model_fp32.pth')}")
print(f"INT8 size: {os.path.getsize('model_int8.pth')}")
```

---

## 📊 Summary
Optimization is about the **Latency vs. Accuracy** trade-off. In many production scenarios, a 0.5% drop in accuracy is acceptable if it results in a 10x speedup and 4x cost reduction.
