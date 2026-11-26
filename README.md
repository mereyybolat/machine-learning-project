# Student Performance Prediction

**Course:** ELCE 455 — Machine Learning with Python  
**Author:** Merey Bolat  

This notebook predicts a student’s final exam score (`Exam_Score`) from academic and socioeconomic factors. After the regression models, it also flags **at-risk** students (score below 65) and reports accuracy, precision, recall, and F1.

---

## Requirements

**Anaconda must be installed** before you run the notebook.

1. Download Anaconda (Python 3): https://www.anaconda.com/download
2. Install Anaconda.
3. Open **Anaconda Navigator** and launch **Jupyter Notebook** (or JupyterLab).

These packages come with Anaconda (or are used by the notebook):

- pandas, numpy, matplotlib, seaborn
- scikit-learn
- joblib

**xgboost** is not always included with Anaconda. The first notebook cell checks for it:

- if xgboost is already installed, it continues;
- if it is missing, the cell installs it with `pip` and then continues.

You do not need to install xgboost by hand.

---

## What to download

Please download **these 2 files** and keep them in the **same folder**.  
Do not put them in different folders.

| # | File name | What it is |
|---|---|---|
| 1 | `Student_Performance_Prediction-notebook.ipynb` | The notebook (open this file) |
| 2 | `StudentPerformanceFactors.csv` | The dataset (6,607 records) |

You do **not** need to download `figures/` or `models/` in advance. Those folders are created automatically after **Run All**.

---

## How to run

Download the two files above (or download the project as a **ZIP** and unzip it).  
Keep the notebook and the CSV in the **same folder**:

```
ELCE_455_Project/
├── Student_Performance_Prediction-Prediction-notebook.ipynb
└── StudentPerformanceFactors.csv
```

### Option A — Anaconda / Jupyter

1. Open **Anaconda Navigator** → **Jupyter Notebook**.
2. In Jupyter, open **that same folder**, then open `Student_Performance_Prediction-notebook.ipynb`.
3. Click **Kernel → Restart & Run All** (or the **Run All** button).
4. Wait until every cell finishes.

### Option B — VS Code, Cursor, Antigravity, or a similar IDE

1. Put the two files in the same folder, **or** unzip the ZIP and open that folder in the IDE (**File → Open Folder**).
2. Open `Student_Performance_Prediction-notebook.ipynb`.
3. Select an Anaconda / Python kernel if the IDE asks for one.
4. Click **Run All**.
5. Wait until every cell finishes.

**Please wait 3–8 minutes.** GridSearchCV for Random Forest and the neural network take time. The notebook is not frozen.

If you use **Google Colab**, upload **both** files into the same working directory before Run All.

---

## What appears after Run All

Two new folders appear next to the two source files:

```
ELCE_455_Project/
├── Student_Performance_Prediction-notebook.ipynb
├── StudentPerformanceFactors.csv
├── figures/          ← all plots (saved automatically)
└── models/           ← trained model (saved automatically)
```

### `figures/` — visualizations

| File | Content |
|---|---|
| `fig1_exam_score_dist.png` | Distribution of exam scores |
| `fig2_correlation_heatmap.png` | Feature correlation heatmap |
| `fig3_hours_vs_score.png` | Hours studied vs exam score |
| `fig4_resource_access_boxplot.png` | Access to resources vs exam score |
| `fig5_feature_importance.png` | Feature importance (Random Forest) |
| `fig6_actual_vs_predicted.png` | Actual vs predicted scores |
| `fig_decision_tree_structure.png` | Decision tree plot |

All figures are also displayed inside the notebook.

### `models/` — saved model

| File | Content |
|---|---|
| `best_student_performance_model.pkl` | Trained scikit-learn pipeline (`joblib`) |

---

## Project contents (Weeks 1–13)

| Week | Topic | In the notebook |
|---|---|---|
| 1 | Introduction | Problem statement |
| 2 | Python setup | Imports, seed, folders |
| 3 | NumPy / pandas / matplotlib | EDA and plots |
| 4 | Supervised learning | 60/20/20 split and `ColumnTransformer` |
| 5 | k-NN | `KNeighborsRegressor` |
| 6 | Linear models | Linear, Ridge, Lasso |
| 7 | Midterm review | Validation comparison vs dummy baseline |
| 8 | Decision trees | `DecisionTreeRegressor` and `plot_tree` |
| 9 | Ensemble learning | AdaBoost, Random Forest, XGBoost |
| 10 | Model selection | Validation search + `GridSearchCV` |
| 11 | Feature selection | Feature importance |
| 12 | Deep learning | `MLPRegressor` |
| 13 | Summary | Test-set table, figures, saved model |

---

## How to read the results

**Regression** (main task): predict `Exam_Score`.

- Metrics: MAE, RMSE, R²
- Strongest models on the held-out test set: **Linear Regression** and **Ridge** (almost identical)
- Ensembles are included for Week 9; they are not the most accurate models on this dataset

**Classification** (extra view): at-risk if `Exam_Score < 65`.

- Metrics: accuracy, precision, recall, F1
- `LogisticRegression` is trained on the 0/1 label
- A regressor can also be turned into a classifier by applying the same threshold 65 to predicted scores
- Those two accuracy/F1 numbers will not match, because logistic learns the class directly and the regressor learns the numeric score

---

## If something fails

| Problem | What to do |
|---|---|
| `StudentPerformanceFactors.csv not found` | Put the CSV in the **same folder** as the notebook. In Jupyter, open that folder first. |
| `No module named xgboost` | Run the **first cell**. It installs xgboost automatically if it is missing. |
| Notebook looks frozen | Wait for GridSearchCV (several minutes). Use **Restart & Run All**. |
| `figures/` or `models/` not next to the notebook | Jupyter was started from another folder. Open Jupyter from the folder that contains the two files. |
