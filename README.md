# 💳 Credit Card Fraud Detection under Extreme Class Imbalance

## 📌 Project Overview
This project focuses on **credit card fraud detection**, a real-world machine learning problem characterized by **extreme class imbalance**.

- **Total transactions:** 284,807  
- **Fraud cases:** 492  
- **Fraud ratio:** ~0.17%

The goal is to **maximize fraud detection (recall)** while **controlling false positives**, which is critical in financial systems.

---

## 📊 Dataset Distribution
| Class | Description        | Count |
|------|--------------------|-------|
| 0    | Non-Fraud          | 284,315 |
| 1    | Fraud              | 492 |

---

## 🛠️ Models Implemented
The following models were implemented and compared **without applying PCA**, preserving full feature information:

### 1️⃣ XGBoost (Class Weighting)
- Used `scale_pos_weight` to handle imbalance
- No synthetic data generation
- Optimized for precision–recall trade-off

### 2️⃣ XGBoost + SMOTE (Baseline & Tuned)
- Applied **SMOTE** only on training data
- Evaluated baseline and fine-tuned versions
- Compared against ANN for robustness

### 3️⃣ Artificial Neural Network (ANN)
- Fully connected feed-forward network
- Trained on original **imbalanced data**
- Decision threshold optimized using **F2-score**
- Focused on **high recall at low false positive rate**

---

## 📐 Evaluation Metrics
Due to severe imbalance, **accuracy is not reliable**.  
The following metrics were emphasized:

- **PR-AUC (Primary metric)**
- **Recall**
- **Precision**
- **F2-Score** (recall-oriented)
- **Recall @ Low FPR (≤ 0.5%)**
- Confusion Matrix

---

## 📈 Model Performance Summary

### 🔹 XGBoost + SMOTE (Fine-Tuned)

PR-AUC: 0.8093
Precision: 0.7945
Recall: 0.7733
F2-score: 0.7838

### 🔹 XGBoost (Class Weight Only)

PR-AUC: 0.7890
Precision: 0.8871
Recall: 0.7333
F2-score: 0.8029


---

### 🔹 Artificial Neural Network (ANN)
PR-AUC: 0.8059
ROC-AUC: 0.9879
Best F2-score: 0.7917
Recall @ FPR ≈ 0.5%: 0.8533


**Confusion Matrix (ANN):**
[[56884 3]
[ 18 57]]


---

## 🔁 Cross-Validation (ANN)
- Performed cross-validation to ensure **generalization**
- Stable PR-AUC and recall across folds
- Confirms ANN is **not overfitting**

---

## 🏆 Final Comparison & Conclusion

| Metric | XGBoost + SMOTE | ANN |
|------|----------------|-----|
| PR-AUC | **0.8093** | 0.8059 |
| Recall | 0.7733 | **0.7600** |
| Precision | 0.7945 | **0.9500** |
| Recall @ Low FPR | ❌ Not optimized | **0.8533** |
| Threshold tuning | Limited | **F2-optimized** |

### ✅ Final Verdict
Although **XGBoost + SMOTE achieves slightly higher PR-AUC**, the **ANN is better suited for real-world deployment** because:

- Higher **precision**
- Much better **recall at low false positive rates**
- No reliance on synthetic data
- Robust threshold optimization

➡️ **ANN outperforms XGBoost in operational fraud detection scenarios**.

---

## 🚀 Key Takeaways
- Accuracy is misleading for imbalanced problems
- PR-AUC and Recall @ Low FPR are critical
- ANN with threshold tuning can outperform tree models
- PCA is not mandatory for strong performance

---

## 📌 Internship Relevance
This project demonstrates:
- Real-world imbalanced ML handling
- Advanced evaluation techniques
- Model comparison & business-driven metrics
- Production-oriented decision making

**Highly suitable for ML / Data Science internship applications.**

---

## 📂 Tech Stack
- Python
- NumPy, Pandas
- Scikit-learn
- XGBoost
- TensorFlow / Keras
- Imbalanced-learn (SMOTE)

---

## 👤 Author
**Chesta Vashishtha**  
B.Tech (3rd Year) | Machine Learning Enthusiast  

