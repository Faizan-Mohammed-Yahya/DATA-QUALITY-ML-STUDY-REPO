# How Data Quality Affects Machine Learning Performance

This project investigates how missing values, duplicate records, outliers,
inconsistent values, and class imbalance affect logistic regression across
two datasets: UCI Adult Income and UCI Chronic Kidney Disease.

Seven experimental conditions compare individual interventions with a
combined pipeline, focusing on performance trade-offs rather than assuming
that cleaning always improves results.

## Research Question

How do missing values, duplicate records, outliers, inconsistent values,
and class imbalance affect classification performance, and do their
effects differ across domains?

## Main Findings

- **Adult Income:** Balanced class weights increased recall from 0.603
  to 0.844, while precision decreased from 0.733 to 0.554. This represents
  a trade-off rather than an improvement across every metric.
- **Chronic Kidney Disease:** Outlier clipping corrected one baseline
  error on the main test split. The consistency of this effect is
  examined using additional random seeds.
- **Overall:** The effects of data-quality interventions depend on the
  dataset, intervention, and evaluation metric.

## Project Phases

- **Phase 1 — Adult Income:** Predict whether annual income exceeds $50,000.
- **Phase 2 — Chronic Kidney Disease:** Predict whether a record is
  labelled CKD or not CKD.

Both phases use logistic regression and compare the following conditions:

| Experiment | Intervention |
|---|---|
| E0 | Baseline with the basic preprocessing required to run the model |
| E1 | Missing-value treatment |
| E2 | Removal of exact duplicate training rows |
| E3 | Outlier treatment using training-set IQR limits |
| E4 | Invalid or inconsistent value treatment |
| E5 | Balanced class weights |
| E6 | Combined selected pipeline: E1, E2, E4, and E5 |

## Repository Contents

- [Phase 1 notebook](Data_quality_ml_research.ipynb)
- [Phase 2 notebook](phase_2_data_quality_notebook.ipynb)
- [Research report](research_report.pdf)
- [Dataset files and documentation](datasets/)
- [Python dependencies](requirements.txt)

## Datasets

The dataset files used in the experiments are stored in `datasets/`.

| File | Purpose |
|---|---|
| `adult.data` | Adult Income records |
| `adult.names` | Adult dataset documentation and category definitions |
| `ckd.csv` | Chronic Kidney Disease records |

Sources:

- [UCI Adult Income](https://archive.ics.uci.edu/dataset/2/adult)
- [UCI Chronic Kidney Disease](https://archive.ics.uci.edu/dataset/336/chronic+kidney+disease)

Both datasets are provided by the UCI Machine Learning Repository
under the CC BY 4.0 licence. Dataset attribution is included in the report.

## Running in Google Colab

1. Open either notebook in Google Colab.
2. Select **Runtime → Run all**.
3. Upload the requested files when the upload prompt appears:
   - Phase 1: `adult.data` and `adult.names`.
   - Phase 2: `ckd.csv`, followed by `adult.data` for the
     cross-domain comparison.

Download these files from this repository's `datasets/` folder first.
The current notebooks load manually uploaded files from the Colab
working directory.

Results, CSV files, and charts are generated in the runtime session.
Download any outputs you want to retain before the session ends.

## Running Locally

Use a Python environment with Jupyter installed.

Install the project dependencies:

    python -m pip install -r requirements.txt

The current notebooks expect dataset files in their working directory.
Copy `adult.data`, `adult.names`, and `ckd.csv` from `datasets/` into
the same directory as the notebooks before running them.

Open the notebooks in Jupyter and run their cells in order.

## Experimental Design and Reproducibility

The main comparison uses random seed 42. Additional seeds are used
to examine sensitivity to the train/test split.

Feature-identical records are kept on the same side of the split
to reduce duplicate leakage. Imputation values, category encoding,
scaling parameters, and outlier limits are learned from training
data only.

The model is held fixed so that comparisons focus on the effects
of the data-quality interventions.

Evaluation metrics include accuracy, precision, recall, F1,
and ROC-AUC.

## Limitations

- The study covers two datasets and one model: logistic regression.
- Additional random splits provide a limited sensitivity check,
  not a statistical significance test.
- The kidney dataset is small, so a single prediction can noticeably
  affect test metrics.
- The findings describe these experiments and should not be treated
  as universal rules.
- The healthcare experiment is an educational analysis, not a
  clinically validated diagnostic system.

## Author

Faizan Mohammed Yahya
