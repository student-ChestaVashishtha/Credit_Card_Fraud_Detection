💳 Credit Card Fraud Detection under Extreme Class Imbalance
📌 Project Overview

This project tackles credit card fraud detection, a real-world machine learning problem with extreme class imbalance (~0.17% fraud). The goal is not high accuracy, but effective fraud detection with minimal false alarms.

Multiple models were implemented, tuned, and evaluated using probability-based, recall-oriented metrics:

XGBoost + SMOTE (tuned)

Artificial Neural Network (ANN) with class-weighted loss and threshold optimization

🎯 Problem Characteristics

Fraud detection is cost-sensitive

False Negatives (missed fraud) → direct financial loss

False Positives → customer inconvenience

Hence, the focus is on:

PR-AUC

Fraud recall

Recall under low false positive rate constraints

F₂ score (recall-weighted)

📊 Dataset

Total transactions: 284,807

Class distribution:

Class	Count
Legitimate (0)	284,315
Fraud (1)	492

Fraud rate ≈ 0.17%

Features: anonymized continuous variables (V1–V28), Time, Amount

⚠️ Due to extreme imbalance, accuracy is not a meaningful metric.

🧠 Models & Training Strategy
1️⃣ XGBoost + SMOTE (Tuned)

Gradient boosting decision trees

Imbalance handled using:

SMOTE (applied only on training data)

Hyperparameter tuning

Evaluated using predicted probabilities

Metrics optimized post-training using threshold-based evaluation

2️⃣ Artificial Neural Network (ANN)

Fully connected binary classifier with sigmoid output

Training strategy:

Class-weighted binary cross-entropy

Early stopping monitored on PR-AUC

Post-training:

Probability-based evaluation

Threshold optimization using F₂ score (β = 2)

Robustness checked using cross-validation

📐 Evaluation Methodology

Because fraud prevalence is only 0.17%:

Accuracy is misleading (>99.8% achievable with trivial models)

Models are evaluated using:

PR-AUC (Average Precision)

Fraud recall

Precision

F₂ score

Recall @ low False Positive Rate (≈ 0.5%)

All metrics are computed from predicted probabilities, not hard class labels.

📈 Results Comparison (Final)
🔹 Tuned XGBoost + SMOTE
PR-AUC     : 0.8093
Precision  : 0.79
Recall     : 0.77
F2-score   : 0.784


Classification summary:

Frauds detected: ~58 / 75

Balanced precision–recall tradeoff

Strong baseline for tabular fraud detection

🔹 Artificial Neural Network (Final Model)
PR-AUC (AP)          : 0.8059
ROC-AUC              : 0.9879
Precision (Fraud)    : 0.95
Recall (Fraud)       : 0.76
Best F2-score        : 0.7917
Recall @ FPR ≈ 0.5%  : 0.8533


Confusion Matrix:

[[56884     3]
 [   18    57]]


Frauds detected: 57 / 75

Only 3 false positives at the selected operating point

🔁 Cross-Validation (ANN)

ANN performance was validated using cross-validation

PR-AUC and recall remained consistent across folds, indicating:

Stable learning

No overfitting to a single split

Reliable probability calibration

🏆 Model Selection & Final Conclusion

Although tuned XGBoost + SMOTE achieved the highest PR-AUC (0.8093), the ANN was selected as the final model because:

Comparable PR-AUC performance

Higher precision (fewer false alarms)

Superior recall at low false positive rate, which is critical in production fraud systems

Stable performance confirmed via cross-validation

This demonstrates that model selection should be driven by operational metrics and deployment constraints, not by algorithm popularity alone.

📌 Final Takeaways

Accuracy is misleading in extreme imbalance scenarios

PR-AUC is the most informative ranking metric for fraud detection

Threshold optimization is essential for real-world deployment

Neural networks can outperform tree models when probability calibration and objectives are aligned

🛠️ Tech Stack

Python

NumPy, Pandas

Scikit-learn

XGBoost

TensorFlow / Keras

Matplotlib

🚀 Future Improvements

Time-based splitting to model data drift

Cost-sensitive loss functions

Probability calibration (Platt / Isotonic)

Real-time fraud detection dashboard

👤 Author

Chesta Vashishtha
B.Tech (3rd Year)
Aspiring Machine Learning Engineer
