# Data Mining Project

This repository contains two Jupyter notebooks that demonstrate common data mining tasks on provided datasets: classification modeling and association rule mining.

## Contents

- `classification_task.ipynb` — end-to-end classification pipeline on `loan_data.csv` (preprocessing, EDA, modeling with Decision Tree, Random Forest, SVM, Logistic Regression, feature engineering and dimensionality reduction).
- `Association_Rule_Mining.ipynb` — demonstrates association rule mining (Apriori / FP-Growth style workflow) on `basket_analysis.csv` using `mlxtend`.
- `loan_data.csv` — dataset used for classification tasks (preprocessed and modeled in the notebook).
- `basket_analysis.csv` — transaction-style dataset used for association rule mining.

## Quick summaries

### `classification_task.ipynb`
- Loads `loan_data.csv`.
- Preprocessing: missing-value handling (example: `loan_int_rate`), one-hot encoding for categorical features, scaling numeric features, and duplicate removal.
- EDA: descriptive statistics, histograms, boxplots, correlation heatmap, analysis of target class balance (`loan_status`).
- Modeling: trains Decision Tree, Random Forest, SVM, and Logistic Regression models. Performs k-fold cross-validation and evaluates on a hold-out test set (accuracy, precision, recall, F1, classification reports).
- Feature engineering: creates new ratio features (e.g., `income_loan_ratio`, `age_emp_ratio`) and applies dimensionality reduction (Chi-square for boolean features and PCA for numerical features).
- Retrains models on the reduced feature set and compares performance before/after feature engineering and reduction. The notebook contains discussion of results and suggested next steps.

### `Association_Rule_Mining.ipynb`
- Loads `basket_analysis.csv` and converts it to a transaction matrix (booleans/integers) for frequent-pattern mining.
- Uses `mlxtend.frequent_patterns.apriori` to find frequent itemsets and `mlxtend.frequent_patterns.association_rules` to generate rules using metrics such as support, confidence, and lift.
- Contains notes about installing `mlxtend` in notebook environments.

## Requirements

Suggested Python environment and packages (tested with Python 3.8+):

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn
- mlxtend

You can install these packages via pip (example):

```bash
python -m pip install pandas numpy scikit-learn matplotlib seaborn mlxtend
```

(Or create a virtual environment and install.)

## How to run

Option 1 — Jupyter Notebook (local):
1. Open a terminal in the repository folder.
2. Start Jupyter: `jupyter notebook`.
3. Open `classification_task.ipynb` or `Association_Rule_Mining.ipynb` and run the cells sequentially.

Option 2 — Google Colab:
- Upload the notebook or mount your Google Drive and run the notebook cells. Note: the notebooks contain some Colab-style file paths; adjust file paths if needed (e.g., point to local `loan_data.csv` / `basket_analysis.csv`).

## Notes & Reproducibility
- The `classification_task.ipynb` includes data preprocessing steps that modify the dataframe in place. Re-running the notebook from a fresh kernel on the original CSV is recommended for reproducibility.
- `Association_Rule_Mining.ipynb` demonstrates `mlxtend` usage and includes a pip install cell for convenience when running in environments like Colab.

## Suggested next steps
- Add a `requirements.txt` or `environment.yml` to freeze package versions for exact reproducibility.
- Convert long-running experiments and model training into scripts or a lightweight CLI for automation.
- Add unit tests for small preprocessing functions (if extracted into Python modules).

## Files changed / created
- `README.md` — this file (created).

## License & Contributions
- No license file is included. Add a LICENSE if you intend to share publicly.
- Contributions: open an issue or submit a pull request with improvements or bug fixes.

---

If you want, I can also:
- Generate a `requirements.txt` with versions based on the current environment you run in.
- Add brief instructions to adapt the notebooks for Colab vs local Jupyter (fixing file paths).
- Create small runnable scripts that reproduce the core experiments non-interactively.
