# 06. Model Monitoring 🛰️⚠️

Unlike standard software, ML models can fail "silently." The code might run perfectly, but the predictions could become useless over time.

## 1. Types of Model Failure 📉

### Data Drift
The statistical properties of the incoming input data change over time. 
- *Example:* A house price predictor trained on 2020 data fails in 2024 because the market (input distribution) has shifted.

### Concept Drift
The relationship between input and output changes, even if the input distribution stays the same.
- *Example:* Consumer behavior changes after a major event (like a pandemic), making old shopping predictions invalid.

---

## 2. What to Monitor? 📊

*   **Prediction Drift**: Tracking the distribution of the model's output labels.
*   **Feature Drift**: Tracking individual input features for distribution shifts.
*   **Service Health**: Latency (ms), Throughput (Requests/sec), Error rates (500s).
*   **Ground Truth (when available)**: If you eventually get the real label, track the actual accuracy/error.

---

## 3. Monitoring Stack 🛠️

*   **Prometheus + Grafana**: Standard for technical monitoring (CPU, RAM, Latency).
*   **Evidently AI / WhyLabs**: Specialized for ML monitoring (plotting drift histograms and calculating PSI/KS statistics).
*   **Great Expectations**: To validate data quality *before* it reaches the model.

---

## 🛠️ Essential Snippet (Data Drift check with Evidently)

```python
from evidently.report import Report
from evidently.metric_preset import DataDriftPreset

# reference: training data, current: last 24 hours of production data
report = Report(metrics=[DataDriftPreset()])
report.run(reference_data=train_df, current_data=prod_df)

# Save as HTML for visualization
report.save_html("drift_report.html")
```

---

## 🧩 Practical Tip
**Always set up alerts!** You don't want to manually check dashboards every day. Configure Slack/Email alerts to trigger when the "Drift Score" exceeds a certain threshold.
