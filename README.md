# NanoTox-InVitro

# Data-Driven Nanosafety: Mapping the Landscape of Inorganic Nanoparticle Toxicity via Large-Scale Machine Learning
Created by Chi-Yun Chen |  Date: November 17, 2026

***Welcome to the Nano-Tox project!***

## Overview
This repository provides all code, curated data, trained models, and results for predicting the cytotoxicity of inorganic nanoparticles using both traditional machine-learning algorithms and neural networks.  
## 📁 Folder Structure
```
Nano-Tox/
├── Data/
│   ├── Raw.csv                      # 9,639 entries, 23 columns (internal dataset)
│   └── ExRaw.csv                    # 1,327 entries, 22 columns (external dataset)
├── Notebooks/
│   ├── 1. Data preprocessing.ipynb
│   ├── 2. Classification.ipynb
│   ├── 3. Regression.ipynb
│   └── 4. Optimal model eval.ipynb
├── Models/
│   ├── CytotoxN_GB.joblib
│   └── ViabilityRE_XGB.joblib
└── README.md
```

## 📝 Repository Structure
 
### Data
The Nano-Tox Database comprises 9,383 records for model training and testing, and 1,327 records for external validation.
 
| File | Entries | Columns | Purpose |
|---|---|---|---|
| `Raw.csv` | 9,639 | 23 | Internal dataset; input for the first half of `1. Data preprocessing.ipynb` |
| `ExRaw.csv` | 1,327 | 22 | External dataset; input for the second half of `1. Data preprocessing.ipynb` |
 
### Notebooks
1. **`1. Data preprocessing.ipynb`** — Adds two variables (molecular weight and electronegativity), feature consolidation, performs data analysis (outlier removal & correlation analysis), and visualization. Produces three machine-learning-ready datasets: `NanoTox_9338.csv`, `NanoTox_9338_2.csv`, and `External1327.csv`.
2. **`2. Classification.ipynb`** — Uses `NanoTox_9338.csv` OR `NanoTox_9338_2.csv` to train models predicting binary cytotoxicity of inorganic nanoparticles. Includes one-hot encoding, t-SNE, seven classification algorithms (CatBoostClassifier, GradientBoostingClassifier, RandomForestClassifier, XGBClassifier, KNeighborsClassifier, SVC, MLPClassifier), train/test splitting, and hyperparameter optimization.
3. **`3. Regression.ipynb`** — Uses  `NanoTox_9338.csv` OR `NanoTox_9338_2.csv` to train models predicting continuous cell viability of inorganic nanoparticles. Includes one-hot encoding, t-SNE, seven regression algorithms (CatBoostRegressor, GradientBoostingRegressor, RandomForestRegressor, XGBRegressor, KNeighborsRegressor, SVR, MLPRegressor), train/test splitting, and hyperparameter optimization.
4. **`4. Optimal model eval.ipynb`** — Performs overall evaluation of the optimal classification and regression models, including external validation and visualizations (prediction distributions, feature importance analysis, and applicability domain).
   **Required files:**
   - `External1327` (from Notebook 1)
   - `ClassX`, `ClassY`, 'Cytotox276_8831' (from Notebook 2)
   - `Regress_X`, `Regress_Y`, and 'Viability93_7012' (from Notebook 3)
   - Optimal models: `Cytotox276_8831.joblib`, Viability93_XGB.joblib` 
 
**Run the notebooks in order** (1 → 4)

## 🌟 Key Features
- **Pythonic & open-source**
- **Large-scale database:** Built on Gul et al. (2021), Bilgi et al. (2023), Martin et al. (2023), Kad et al. (2022), and Yildirim et al. (2025), together with newly collected data entries. All data were carefully curated, cross-checked, corrected, and imputed.
- **Multiple algorithms, comprehensive analysis & visualization:** From raw data exploration through detailed model performance assessment, complete with publication-quality figures.

## 🚀 Requirements
These notebooks are intended to run on HiPerGator via Slurm/Open OnDemand, which launches a Jupyter Notebook server on a compute node.
 
**Recommended resources:**
- CPU ≥ 16 cores
- RAM ≥ 120 GB

**Software:**
- Python 3.10.12
- Libraries: `pandas`, `numpy`, `scikit-learn`, `rdkit-pypi`, `seaborn`, `shap`

> **Note:** If you are using Python < 3.10, you may encounter syntax errors where f-strings are used. These can be resolved by rewriting the affected strings using your preferred string-formatting method.

## Questions and Feedback
Questions and feedback are welcome. Please contact Dr. Zhoumeng Lin (linzhoumeng@ufl.edu) or Chiyun Chen (chen.chiyun@ufl.edu), or open a discussion in GitHub Discussions.
 
## Citation
If you find this data or code useful for your research, please consider citing it.
_Chen CY, Lin Z. Data-Driven Nanosafety: Mapping the Landscape of Inorganic Nanoparticle Toxicity via Large-Scale Machine Learning. Under review_
