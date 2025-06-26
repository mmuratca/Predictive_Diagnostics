# System Health Diagnostics via Deep Learning

This project predicts a numerical **System Health Score** from engineering metrics like system complexity, automation usage, and architecture changes. The model leverages deep learning and explainability tools to assess device readiness and reliability.

---

## 🔍 Objective

To detect and predict health degradation risk across hardware systems using structured metrics before validation failures or customer defects occur.

---

## 📦 Setup

```bash
pip install -r requirements.txt
```

> Ensure `hardware_diagnostics_data.xlsx` exists in the root directory under sheet `CleanForSVE`.

---

## 🚀 Run

```bash
python System_Health_Diagnostics_Model.py
```

The script will:
- Perform leave-one-device-out training and prediction
- Save predictions to: `System_Health_Diagnostics_Predictions.xlsx`
- Display SHAP explanation plots

---

## 🧠 Model Overview – System Health Diagnostics

This model predicts a numeric **System Health Score** using device-level metrics such as architectural flags, complexity levels, and logic changes. It’s suited for structured AI use cases in hardware, systems QA, or product validation.

### 🧱 Architecture

| Layer Type         | Configuration |
|--------------------|---------------|
| `LSTM`             | 64 units, `return_sequences=True` |
| `Flatten`          | Converts sequence output to dense input |
| `Dropout`          | `Dropout(0.2)` to prevent overfitting |
| `Dense (hidden)`   | `Dense(64, activation='relu')` |
| `Dense (output)`   | `Dense(1)` for regression output |

---

### ⚙️ Training Configuration

| Component          | Value |
|--------------------|-------|
| **Optimizer**      | `Adam` (default) |
| **Loss Functions** | `mae`, `mse`, `categorical_crossentropy` |
| **Framework**      | TensorFlow 2.x + Keras |
| **Epochs**         | 30 |
| **Validation**     | Leave-One-Device-Out Cross Validation |

---

### 🔍 Explainability & Visualization

| Tool         | Description |
|--------------|-------------|
| **SHAP**     | Used to explain model predictions and rank feature importance |
| **matplotlib / seaborn** | Plots actual vs predicted values, feature relationships |

---

### 📊 Outputs

- `System_Health_Diagnostics_Predictions.xlsx` with per-device predictions and error
- SHAP visual summaries per device

> This model is fully explainable, production-conscious, and ready for expansion into LLM and vector retrieval pipelines in Phase 2.

---

## 📁 Project Structure (Phase 2 next)

```
SystemHealthDiagnostics/
├── src/
│   ├── model_builder.py
│   ├── predictor.py
│   ├── explainer.py
│   ├── data_loader.py
│   └── utils/
├── experiments/
│   ├── configs/
│   └── runs/
├── notebooks/
├── reports/
│   └── shap_visuals/
├── outputs/
│   └── System_Health_Diagnostics_Predictions.xlsx
├── README.md
├── requirements.txt
└── roadmap.md   ← This doc
```
