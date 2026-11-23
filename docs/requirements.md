# Requirements

Last updated: 23 Nov 2026

This is my list of what ClinicalGate needs to do before I can call it finished. I wrote it at the start so I had something to check the project against, and so I knew what to drop if I ran short of time.

I've marked each one Must, Should, Could or Won't. Musts are the minimum for the project to make sense. Shoulds I want but could live without. Coulds only happen if I'm ahead of schedule. Won'ts are things I've decided not to do this time.

## What it needs to do

| ID | Requirement | Priority | How I'll know it's done |
|---|---|---|---|
| FR-01 | Pull one row per ICU stay out of the patient, hospital, apachePatientResult and apacheApsVar tables with SQL | Must | No stay appears twice (test for this) |
| FR-02 | Apply the cohort rules (adults, first ICU stay per admission, APACHE data present) and show how many stays each rule removes | Must | Cohort table in the data readiness report |
| FR-03 | Show data quality per hospital and region: number of stays, missing or invalid values, death rate | Must | Gate G1 |
| FR-04 | Only use information available in the first 24 hours of the stay | Must | Feature allow-list, checked before training |
| FR-05 | Split hospitals into development and external groups using stay counts only, before looking at outcomes | Must | Split file committed before the first model run |
| FR-06 | Train a logistic regression baseline and a random forest on the development hospitals only | Must | Cross-validated AUC recorded |
| FR-07 | Pick the decision threshold on development data and lock it before testing on other hospitals | Must | Threshold saved before the validation run |
| FR-08 | Report AUC, sensitivity and specificity on the external hospitals, overall and by region, with confidence intervals | Must | Gates G2 to G5 |
| FR-09 | Compare my model with the APACHE IV score already in the data | Must | Gate G8 |
| FR-10 | Check performance by sex and age group, and show how many patients are in each group | Must | Gate G6 |
| FR-11 | Show every release gate as pass, fail or not enough evidence, and give a final release decision | Must | All gates |
| FR-12 | Simulate new batches of data coming in and flag when the data starts to look different | Should | Drift report |
| FR-13 | Simulate performance after release and flag when it drops below the gates | Should | Monitoring report |
| FR-14 | Write a model card and a data card | Must | Gate G9 |
| FR-15 | Build a Streamlit app with pages for the overview, data, validation, subgroups, monitoring and release decision | Must | I click through every page on the deployed app |
| FR-16 | Track experiments in MLflow | Could | Only if Sprint 1 finishes early |
| FR-17 | Use the vital signs or nurse charting time series | Won't | Too big for this timeline |

## How well it needs to work

| ID | Requirement | Priority | How I'll check |
|---|---|---|---|
| NFR-01 | Someone else can clone the repo, install requirements.txt and get the same results (fixed random seeds) | Must | Clone it into a new folder and run it |
| NFR-02 | Every number in the app comes from a file a script produced, nothing typed in by hand | Must | The app only reads from reports/ |
| NFR-03 | No leakage: preprocessing is fitted on development data only, and external hospitals are never used for training or tuning | Must | Code review and a pipeline test |
| NFR-04 | The app and README say clearly that this is a prototype on public historical data, not clinically validated and not a medical device | Must | Check the overview page and README |
| NFR-05 | The eICU demo is credited properly under its ODbL licence | Must | LICENSE.txt kept in data/raw, citation in README |
| NFR-06 | Only the open demo data goes in the repo | Must | Check data/raw before each push |
| NFR-07 | Someone non-technical can follow the overview and release decision pages | Should | Ask a friend to read them |
| NFR-08 | Each page loads in under 5 seconds once deployed | Should | Time it on Streamlit Cloud |
| NFR-09 | Code is split into modules with tests for the data checks, pipeline and predictions | Should | pytest passes |
| NFR-10 | The app stays online while I'm applying and interviewing | Should | Check the link before each interview |
