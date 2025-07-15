# 🧪 Machine Learning Pipeline with DVC and MLflow

This project demonstrates a complete machine learning workflow using **DVC** for data and model versioning and **MLflow** for experiment tracking. It centers on training a **Random Forest Classifier** on the **Pima Indians Diabetes Dataset**, with distinct stages for preprocessing, training, and evaluation.

---

## 🚀 Key Highlights

### ✅ Data Versioning with DVC
- Tracks datasets, models, and pipeline stages for reproducibility.
- Automatically re-runs stages when code, data, or parameters change.
- Supports remote storage (e.g., DagsHub, S3) for large files.

### 📊 Experiment Tracking with MLflow
- Logs hyperparameters, evaluation metrics, and artifacts.
- Enables comparison of multiple runs and model versions.
- Supports optimization through insightful experiment tracking.

---

## 🧩 Pipeline Overview

### 1️⃣ Preprocessing
- **Script**: `src/preprocess.py`
- **Input**: `data/raw/data.csv`
- **Output**: `data/processed/data.csv`
- Prepares consistent, structured data for training.

### 2️⃣ Training
- **Script**: `src/train.py`
- **Model**: Random Forest Classifier
- **Output**: `models/model.pkl`
- Logs model and configuration to MLflow.

### 3️⃣ Evaluation
- **Script**: `src/evaluate.py`
- **Metric**: Accuracy
- Evaluates model performance and tracks results in MLflow.

---

## 🎯 Project Goals
- **Reproducibility**: DVC ensures consistent, repeatable results across environments.
- **Experimentation**: MLflow empowers rapid iteration and performance analysis.
- **Collaboration**: Shared tracking and versioning improve teamwork and transparency.

---

## 🛠️ Technology Stack

| Tool          | Purpose                                 |
|---------------|------------------------------------------|
| Python        | Core programming language                |
| DVC           | Version control for data and models      |
| MLflow        | Experiment logging and tracking          |
| Scikit-learn  | Random Forest model implementation       |

---

## 👥 Use Cases

- **Data Science Teams**: Organize and manage data, models, and experiments.
- **ML Researchers**: Run and compare multiple experiments with minimal overhead.

---

## 📌 DVC Stage Configuration

```bash
# Preprocessing Stage
dvc stage add -n preprocess \
    -p preprocess.input,preprocess.output \
    -d src/preprocess.py -d data/raw/data.csv \
    -o data/processed/data.csv \
    python src/preprocess.py

# Training Stage
dvc stage add -n train \
    -p train.data,train.model,train.random_state,train.n_estimators,train.max_depth \
    -d src/train.py -d data/raw/data.csv \
    -o models/model.pkl \
    python src/train.py

# Evaluation Stage
dvc stage add -n evaluate \
    -d src/evaluate.py -d models/model.pkl -d data/raw/data.csv \
    python src/evaluate.py
```

---

This project exemplifies how to structure, manage, and reproduce machine learning pipelines reliably. For further enhancements, consider integrating model deployment and automated testing.

