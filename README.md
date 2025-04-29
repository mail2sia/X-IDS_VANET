# X-IDS: An explainable ensemble-based intrusion detection system for software-deﬁned vehicle ad-hoc networks.
This repository accompanies the research article:

**S.I. Ahsan, P. Legg, S.M.I. Alam**  
*"An explainable ensemble-based intrusion detection system for software-defined vehicle ad-hoc networks"*  
**Cyber Security and Applications, 2025**  
🔗 [Link to Article](https://doi.org/10.1016/j.csa.2025.100090)

---

## Overview

This work presents an **explainable ensemble-based Intrusion Detection System (IDS)** for **Software-Defined VANETs (SD-VANETs)**.  
We combine:
- **Random Forest (RF)** and **CatBoost** as base models,
- **Logistic Regression (LR)** as the final meta-classifier,
- **SHAP (SHapley Additive exPlanations)** for explainability analysis.

The system is trained and evaluated on the **VeReMi dataset**, achieving strong detection rates with explainable model behaviour.

---

## Repository Contents

- `X-IDS_StackingClassifier.ipynb`: Full model training, evaluation, and SHAP analysis.
- `Classification_Report.PNG`: Classification report (precision, recall, F1-score, support).
- `Confusion_Matrix.PNG`: Confusion matrix visualization.
- `Detection_Accuracy.PNG`: Class-wise detection accuracy results.
- `SHAP_CatBoost.PNG`: SHAP interaction summary plot for CatBoost.
- `SHAP_RF.PNG`: SHAP interaction summary plot for Random Forest.
- `1-s2.0-S2772918425000074-main.pdf`: Full published research paper.

---
## Dataset
Vehicular Reference Misbehavior (VeReMi) Dataset

📥 [Official Website](https://veremi-dataset.github.io/)

Reference:
V. van der Heijden, S. Dietzel, T. Leinmüller, F. Kargl,
"VeReMi: A Dataset for Misbehavior Detection in VANETs",
Proceedings of the 6th ACM Symposium on Development and Analysis of Intelligent Vehicular Networks and Applications (DIVANet'16).

---
## Main Contributions

- **Stacked Ensemble Approach**:  
  Integration of Random Forest, CatBoost, and Logistic Regression.

- **Explainability with SHAP**:  
  SHAP interaction plots reveal how different features contribute to classification decisions.

- **High Detection Performance**:  
  - **Cross-validation Accuracy**: 98.83% ± 0.08%
  - **Overall Multiclass Accuracy**: 98.11%
  - **Binary Classification Accuracy**: 99.68%
  - **Attack-wise Detection Accuracy**:
    - BENIGN: 97.65%
    - Constant Attack: 100.00%
    - Constant Offset Attack: 99.74%
    - Eventual Stop Attack: 97.14%
    - Random Attack: 99.95%
    - Random Offset Attack: 99.10%

- **Analysis of Misclassifications**:  
  Eventual Stop Attack showed slightly lower precision (78%) compared to other attack types.

---

## Getting Started

### Requirements

- Python 3.8+
- scikit-learn
- catboost
- shap
- matplotlib
- seaborn
- numpy
- pandas

```bash
pip install scikit-learn catboost shap matplotlib seaborn numpy pandas
```

### Running

Open and run `X-IDS_StackingClassifier.ipynb` to reproduce the results.

---

## Results Summary

| Attack Type             | Precision | Recall | F1-Score |
|--------------------------|-----------|--------|----------|
| BENIGN                   | 100%      | 98%    | 99%      |
| Constant Attack          | 100%      | 100%   | 100%     |
| Constant Offset Attack   | 99%       | 100%   | 99%      |
| Eventual Stop Attack     | 78%       | 97%    | 87%      |
| Random Attack            | 100%      | 100%   | 100%     |
| Random Offset Attack     | 98%       | 99%    | 99%      |

- **Macro-averaged F1-Score**: 97.14%  
- **Weighted-averaged F1-Score**: 98.28%

Detection Accuracies:
- BENIGN: 97.65%
- Constant Attack: 100.00%
- Constant Offset Attack: 99.74%
- Eventual Stop Attack: 97.14%
- Random Attack: 99.95%
- Random Offset Attack: 99.10%

---

## SHAP Analysis

- **Random Forest (SHAP_RF.PNG)**:
  - Most influential features: `pos-x1`, `pos-y1`, `spd-x1`, and `spd-y1`.
  - Features `sender_1` and `messageID` had lower interaction importance.

- **CatBoost (SHAP_CatBoost.PNG)**:
  - Strong interactions observed for `pos-x1`, `pos-y1`, and `spd-y1`.
  - Clusters formed clearly distinguish benign versus attack traffic.

- **Observations**:
  - **pos-x1** and **pos-y1** coordinates were critical for attack detection.
  - **Eventual Stop Attack** misclassifications mostly linked to overlapping position-based features.
  - Minor confusion between BENIGN and Eventual Stop Attack categories in confusion matrix.

---

## Citation

```bibtex
@article{Ahsan2025XIDS,
  title={An explainable ensemble-based intrusion detection system for software-defined vehicle ad-hoc networks},
  author={Shakil Ibne Ahsan and Phil Legg and S.M. Iftekharul Alam},
  journal={Cyber Security and Applications},
  volume={3},
  pages={100090},
  year={2025},
  publisher={Elsevier}
}
```

---
