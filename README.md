# Premature Neonatal Mortality Prediction

Research question: Do machine learning algorithms based on EHR data outperform accepted clinical risk scores in predicting in-hospital mortality of premature babies who are transferred to the NICU at Beth Israel Deaconess Medical Center?

This project was conducted using the MIMIC-IV v1.0 EHR dataset from Beth Israel Deaconess Medical Center (https://physionet.org/content/mimiciv/1.0/).

This repository is organized into the following notebooks and directories:
- `cohort-builder`: notebook with functions and code to construct cohorts of premature neonates meeting our eligibility criteria given a Time 0
- `modeling`: notebook with functions and code to run our modeling pipeline, which consists of data splitting, data preprocessing, and model training and evaluation on a given cohort and feature set
- `logs-analysis`: notebook with code to graph comparison plots to analyze model results from log files
- `eda`: notebook with unorganized code that was used in initial exploratory data analysis in an effort to understand our EHR data and our cohort
- `cohorts`: directory with CSV files for the cohorts produced from `cohort-builder`; these files can be used directly by `modeling` so cohort does not need to be rebuilt each time
- `logs`: directory with JSON files for the logs produced from `modeling` with training/validation/testing metrics for each experiment run, organized in subdirectories by cohort and feature set; these files can be used by `logs-analysis`
