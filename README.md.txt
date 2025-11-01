 Fraud Detection via Stacking Ensemble with SHAP Interpretability

This repository contains the full implementation of a hybrid stacking ensemble model for detecting fraudulent financial transactions. The framework integrates  LightGBM, HistGradientBoosting , and  Logistic Regression , optimized using **Optuna  and evaluated through  time-based cross-validation**. Model interpretability is achieved using **SHAP (SHapley Additive exPlanations)  to ensure transparency and trustworthiness.

 Overview

With the rise of digital payments, fraud detection has become a critical challenge for financial institutions. This project addresses key limitations in prior work by:

 Employing  temporal validation  to simulate real-world deployment.
Handling  class imbalance  using  ADASYN  within each fold to prevent data leakage.
Leveraging  SHAP  for feature-level interpretability.
Achieving  near-perfect performance** on structured transaction data.

 Model Architecture

Base Learners**:  
LightGBMClassifier`  
HistGradientBoostingClassifier`

*Meta-Learner
LogisticRegression` (via `StackingClassifier`)

Optimization
Optuna` with `StratifiedKFold` (2-fold) and `F1-score` as the objective.

Validation Strategy
TimeSeriesSplit` (5 folds) to preserve chronological order.

Interpretability
TreeSHAP` for LightGBM  
KernelSHAP` for HistGradientBoosting

 Project Structure

---

## 📦 Installation

```bash
git clone https://github.com/your-username/fraud-detection-stacking.git
cd fraud-detection-stacking
pip install -r requirements.txt
-Usage
Run the notebook or script to:

Load and preprocess the dataset.

Apply ADASYN within each temporal fold.

Train the stacking ensemble.

Evaluate performance using F1, ROC AUC, MCC, and Balanced Accuracy.

Visualize SHAP values for interpretability.

 -Dataset
This project uses the Online Payments Fraud Detection dataset available on Kaggle. A random sample of 200,000 transactions was selected to ensure computational efficiency while preserving class diversity. https://www.kaggle.com/code/ananthu19/online-payments-fraud-detection
-Sample Results
F1-Score: > 0.97
ROC AUC: ≈ 0.999
MCC: High correlation across folds
Top Features: amountRatioOrig, balanceDiffOrig, newbalanceOrig
 -Interpretability
SHAP analysis confirmed that the model’s decisions are grounded in domain-relevant patterns, such as:
Disproportionate transaction-to-balance ratios
Abrupt balance changes post-transaction

-Limitations
Evaluated on a single dataset; external validation is needed.

Synthetic oversampling may introduce bias.

Sequential dependencies not explicitly modeled.

Controlled conditions may not reflect real-time deployment noise.

-  Citation
If you use this work in your research, please cite:
Abdelali, M.M. (2025). Fraud Detection via Stacking Ensemble with SHAP Interpretability. GitHub Repository. https://github.com/MohamedAlobede/fraud-detection-stacking
Author
Mohammed Mustafa AbdulAli Lecturer & Applied Researcher in AI and Network Security Higher Institute of Science and Technology, Musaid 📧 Contact: [mohamdabdulali@proton.me]
  



