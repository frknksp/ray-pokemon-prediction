# ⚡ Ray Pokemon Prediction: Distributed ML Pipeline

## 📖 Overview
This project implements a **Distributed Machine Learning Pipeline** to predict Pokemon spawns (151 Classes) based on geospatial and environmental data.

By leveraging **Ray Core** for task parallelism and **LightGBM** for efficient gradient boosting, this project demonstrates how to scale hyperparameter optimization on multi-core CPU clusters.

The final model achieves **~19x lift** over random guessing and successfully identifies rare Pokemon spawns using a balanced class weight strategy and deep decision trees.

---

## 🏗️ Architecture

This project moves beyond traditional sequential training by using **Task Parallelism**:

| Component | Technology | Role in Project |
| :--- | :--- | :--- |
| **Orchestration** | **Ray Framework** | Manages distributed execution. Enables training 5+ models simultaneously. |
| **Object Store** | **Ray Plasma Store** | Provides **Zero-Copy Serialization**, allowing workers to share the training data (RAM) without duplication. |
| **Model** | **LightGBM** | Uses **Native Categorical Support** to handle high-cardinality `cellId` features efficiently. |

---

## 📊 Key Results

| Metric | Random Guessing | **Ray (LightGBM - Config 3)** | Improvement |
| :--- | :--- | :--- | :--- |
| **Accuracy** | ~0.66% | **12.74%** | **~19x** |
| **F1 Score** | ~0.006 | **0.1181** | **High** |

> **Feature Importance:** The model revealed that **Geospatial Location (`cellId`)** is the most critical factor (33.8%), followed by proximity to **Pokestops/Gyms (32%)**.

