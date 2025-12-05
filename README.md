# Premature Neonatal Mortality Prediction

Research question: Do machine learning algorithms based on EHR data outperform accepted clinical risk scores in predicting in-hospital mortality of premature babies who are transferred to the NICU at Beth Israel Deaconess Medical Center?

This project was conducted using the MIMIC-IV v1.0 EHR dataset from Beth Israel Deaconess Medical Center.

This repository is organized into the following notebooks:
- `cohort-builder`: notebook with functions and code to construct cohorts of premature neonates meeting our eligibility criteria given a Time 0
- `modeling`: notebook with functions and code to run our modeling pipeline, which consists of data splitting, data preprocessing, and model training and evaluation on a given cohort and feature set
- `logs-analysis`: notebook with code to graph comparison plots to analyze model results from log files
- `eda`: notebook with unorganized code that was used in initial exploratory data analysis in an effort to understand our EHR data and our cohort

In addition, there are the following directories:
- `cohorts`: directory with CSV files for the cohorts produced from `cohort-builder`; these files can be used directly by `modeling` so cohort does not need to be rebuilt each time
- `logs`: directory with JSON files for the logs produced from `modeling` with training/validation/testing metrics for each experiment run, organized in subdirectories by cohort and feature set; these files can be used by `logs-analysis`
- `docs`: directory for documentation, such as our project report and diagrams

Here are the steps to run our full cohort study from scratch:
1. Build your cohort in `cohort-builder`, specifying a Time 0 in the appropriate variable (e.g., `12`) &rarr; this will save your final cohort as a CSV file in `cohorts`
2. Run the modeling pipeline in `modeling`, specifying the cohort (e.g., `cohort_t12`) and features to include &rarr; this will save your experiment results as JSON files in `logs` under your cohort and feature set
3. Analyze your experiment results in `logs-analysis` to produce plots of your results for model performance comparison

These steps already assume you have the [MIMIC-IV v1.0](https://physionet.org/content/mimiciv/1.0/) data downloaded; if not, you must download the following data files:
- `core/patients.csv`
- `core/admissions.csv`
- `core/transfers.csv`
- `hosp/d_icd_diagnoses.csv`
- `hosp/diagnoses_icd.csv`
- `hosp/d_labitems.csv`
- `hosp/labevents.csv`

Our cohort study design and eligibility criteria are as follows:

![](https://github.com/irith-kat/NICU-MP/blob/main/docs/cohort-study-design.png?raw=true)
![](https://github.com/irith-kat/NICU-MP/blob/main/docs/cohort-eligibility-criteria.png?raw=true)
