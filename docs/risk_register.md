# Risk Register

Last reviewed: 23 Nov 2026 (I go through this at every sprint review)

These are the things I think could go wrong, how likely and how bad each one is, and what I'm doing about it.

I score likelihood (P) and impact (I) from 1 to 5 and multiply them. 15 or more is red, 8 to 14 amber, under 8 green. I don't delete risks when they're done, I just change the status.

| ID | Risk | P | I | Score | What I'm doing about it | Owner | Status |
|---|---|---|---|---|---|---|---|
| R01 | Information from after the first 24 hours (discharge time, length of stay, the actual outcome) slips into the features | 3 | 5 | 15 Red | Keep a written list of allowed features and check it before any training | ML Engineer | Open |
| R02 | Missing APACHE values are stored as -1 or blank and get treated as real numbers | 4 | 4 | 16 Red | Do the data readiness report first and convert these codes to missing | ML Engineer | Open |
| R03 | Joins duplicate patients. I already saw this: apachePatientResult has 3,676 rows but only 2,205 stays have APACHE data | 4 | 4 | 16 Red | Filter to one APACHE version and add a test that checks one row per stay | ML Engineer | Open |
| R04 | Too few deaths per hospital, so the results jump around | 4 | 3 | 12 Amber | Pool the external hospitals for the gates, use bootstrap intervals, and mark small regions as not enough evidence | ML Engineer | Open |
| R05 | Some subgroups are too small for the fairness check to mean much | 3 | 3 | 9 Amber | Show the group size next to every result and avoid calling the model fair just because numbers look close | ML Engineer | Open |
| R06 | The model fails one or more release gates | 3 | 2 | 6 Green | That's an acceptable result. I'll record why and what I'd do next | QA and Regulatory | Open |
| R07 | Switching to eICU adds data work and pushes the schedule | 3 | 3 | 9 Amber | Stick to the patient and APACHE tables and leave the time series out | Project Manager | Open |
| R08 | I keep adding things (more tables, MLflow, extra pages) | 3 | 4 | 12 Amber | New ideas go in the backlog, not the current sprint | Project Manager | Open |
| R09 | Work shifts and job applications eat into project time | 3 | 3 | 9 Amber | Aim for 5 hours a day and keep 9 Dec free as a buffer | Project Manager | Open |
| R10 | Package versions clash or Streamlit Cloud deployment fails | 2 | 3 | 6 Green | Pin versions in requirements.txt and deploy a basic version in Sprint 1, not at the end | ML Engineer | Open |
| R11 | Someone reads the results as clinical evidence | 2 | 4 | 8 Amber | Put the limitations on the app overview, README and model card | QA and Regulatory | Open |
| R12 | I accidentally delete Jira items or files | 2 | 2 | 4 Green | Check the count before any bulk action and commit often | Project Manager | Happened on 23 Nov, items recreated |

Owners are the roles I'm playing at the time, since I'm doing this project on my own.
