# ClinicalGate: Clinical AI Validation and Release Tracker

**Status:** In development (Sprint 0, November 2026)

ClinicalGate simulates how a healthcare AI company decides whether a machine learning model is ready to release. A model that predicts in-hospital death for ICU patients is developed on hospitals from one US region and then tested, without retraining, on hospitals it has never seen.

## Why this project

A model that performs well at some hospitals can perform worse at others, because patients, case mix and recording practices differ. Before release, a team needs to check data quality, prevent data leakage, validate on unseen sites, look for differences between patient groups, and agree clear release criteria. ClinicalGate puts that process into one application.

## What it will do

1. Data extraction with SQL: one row per ICU stay from the eICU relational tables
2. Data readiness: cohort rules, missing values and differences between hospitals
3. Model development on one region's hospitals, using only first-24-hour information
4. External validation on unseen hospitals, compared with the APACHE IV clinical score
5. Subgroup analysis by sex and age
6. Release gates with pass or fail results, fixed before any results were seen
7. Simulated post-release monitoring for data drift and performance changes

## Data

eICU Collaborative Research Database Demo, version 2.0.1: over 2,500 ICU stays from 20 US hospitals, 2014 to 2015. Open access under the Open Database License (ODbL) v1.0.

Johnson, A., Pollard, T., Badawi, O., & Raffa, J. (2021). eICU Collaborative Research Database Demo (version 2.0.1). PhysioNet. https://doi.org/10.13026/4mxk-na84

Only four tables are used: patient, hospital, apachePatientResult and apacheApsVar.

## Limitations

This is a portfolio prototype built on public, retrospective data. It is not clinically validated, is not a medical device, and makes no claims about patient benefit or clinical safety. Deployment and monitoring are simulated. The demo contains a small number of stays per hospital, so results carry wide uncertainty.

## Project management

Delivered in three sprints (22 November to 8 December 2026) using a Jira Scrum board. Release criteria are in `docs/release_gates.md`.

## Tech stack

Python, SQL (SQLite), pandas, NumPy, scikit-learn, SciPy, Plotly, Matplotlib, Streamlit, pytest

## How to run

To be added once the first app page is built.

## Author

Aleena Khalid, MSc Artificial Intelligence, Queen Mary University of London
[LinkedIn](https://www.linkedin.com/in/aleenakhalid03)
