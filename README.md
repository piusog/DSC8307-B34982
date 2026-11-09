# DSC8307  Data Mining, Modeling and Analytics: Advent 2026

**Student:** Pius OGWAL  
**Access number:** B34982  
**Programme:** Master of Science in Data Science and Analytics, Year 2, Semester 1

## Contents
- `project1_bank_marketing.ipynb`: bank subscription classification, baselines, three models, cross-validation, threshold/cost sensitivity and diagnostics.
- `project2_concrete_strength.ipynb`: concrete strength regression, mean baseline, linear/nonlinear comparisons, residuals, robustness and causality.
- `requirements.txt`: reproducible Python environment.
- `data/`: input datasets (see below).

## Reproduce
Use Python 3.11+ and run:

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
python -m pip install -r requirements.txt
jupyter notebook
```

Open each notebook and select **Restart Kernel and Run All**. For a command-line check:

```bash
jupyter nbconvert --to notebook --execute project1_bank_marketing.ipynb --output project1_executed.ipynb --ExecutePreprocessor.timeout=1800
jupyter nbconvert --to notebook --execute project2_concrete_strength.ipynb --output project2_executed.ipynb --ExecutePreprocessor.timeout=1800
```

## Data
Place the following in `data/`:
- `bank-additional-full.csv` (semicolon-delimited), from the UCI Bank Marketing archive: https://archive.ics.uci.edu/dataset/222/bank+marketing
- `Concrete_Data.csv`, from the UCI Concrete Compressive Strength dataset: https://archive.ics.uci.edu/dataset/165/concrete+compressive+strength

If absent, notebooks attempt to download official UCI archives and cache the CSV locally. Internet access is needed for the automatic fallback. **Both datasets are in `data/`, and both notebooks ran successfully with results embedded. **** Confirm redistribution rights and required attribution for each dataset before making the repository public.

## Attribution
Moro, S., Cortez, P., & Rita, P. (2014), *Decision Support Systems*, 62, 22–31. https://doi.org/10.1016/j.dss.2014.03.001  
Yeh, I.-C. (1998), *Cement and Concrete Research*, 28(12), 1797–1808. https://doi.org/10.1016/S0008-8846(98)00165-3  
UCI Machine Learning Repository and scikit-learn documentation.

## Observed results (seed 42, supplied CSVs)

| Analysis | Main findings |
|---|---|
| Bank classification | 41,188 rows; subscription prevalence 11.27%; gradient boosting test PR-AUC 0.4826, ROC-AUC 0.8081; validation cost-sensitive threshold 0.175 under illustrative 1:5 FP:FN costs |
| Concrete regression | 1,030 source rows, 25 exact duplicates removed before splitting; gradient boosting test MAE 3.431 MPa, RMSE 5.025 MPa, R² 0.915 |
