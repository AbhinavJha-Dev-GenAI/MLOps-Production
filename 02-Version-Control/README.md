# 02. Version Control for ML 🗄️📦

Standard software uses Git for code. ML requires versioning for **Code**, **Data**, and **Models** simultaneously.

## 1. The Problem: Git ❌ Data 

Git is designed for text files. Storing 100GB datasets or 500MB model weights in Git leads to:
- Huge repository sizes.
- Extremely slow clones and pulls.
- LFS (Large File Storage) limits.

---

## 2. DVC (Data Version Control) 🏛️

DVC allows you to version your data and models just like you version your code, but without storing the actual binary files in Git.

### How it works:
1.  **Code** stays in **Git**.
2.  **Data/Models** stay in **Remote Storage** (S3, GCS, Azure Blob).
3.  **Meta-files (`.dvc`)** created by DVC are lightweight text files stored in **Git** that point to the specific version of the data in remote storage.

---

## 3. Data Lineage 🧬

DVC creates a DAG (Directed Acyclic Graph) of your pipeline. This ensures that:
- You know exactly which version of the raw data produced which features.
- You know exactly which features produced which specific model version.

---

## 🛠️ Essential Snippet (Basic DVC Workflow)

```bash
# 1. Initialize
dvc init

# 2. Add a giant dataset
dvc add data/raw_dataset.csv

# 3. Commit the .dvc file to Git
git add data/raw_dataset.csv.dvc .gitignore
git commit -m "Add raw dataset version 1.0"

# 4. Push actual data to S3
dvc remote add -d myremote s3://my-bucket/dvcstore
dvc push
```

---

## ⚖️ Why this Matters
Reproducibility is the core of MLOps. If you can't go back to the exact dataset version that produced a production model, you can't debug a production failure.
