# Phase II Clinical Trial Data Management Portfolio

**Mock study:** Randomized, 2-arm Phase II trial of an oral antidiabetic agent ("Drug X") vs. Standard Therapy in Type 2 Diabetes Mellitus (T2DM)
**Role simulated:** Clinical Data Manager / CRA-support data review
**Subjects:** 100 (50 per arm, 2 sites) | **Visits:** 700 visit records across 7 protocol timepoints (Screening → Week 24)

> This is a **mock/synthetic dataset** built to practice and demonstrate core Clinical Data Management (CDM) and Clinical Research Associate (CRA) skills: data reconciliation, query management, edit check design, protocol deviation tracking, and database lock readiness review. No real patient data is used.

---

## Why this project

I'm building toward an entry-level Clinical Data Manager / CRA role. Rather than just listing "attention to detail" and "GCP knowledge" on a resume, this project shows the actual deliverables a data management associate produces during a live study: cross-form reconciliation, an edit check specification, a query log analysis, and a lock-readiness checklist.

## What's in this repo

| Folder | Contents |
|---|---|
| `/data` | Source workbook — `Mock_PhaseII_Clinical_Trial_Final.xlsx` (11 sheets: Demographics, Visits, Adverse Events, Concomitant Medications, Protocol Deviations, Withdrawals, Drug Accountability, Query Log, Data Dictionary) |
| `/reports` | `01_Data_Reconciliation_Report.md` — cross-form data quality checks with results<br>`02_Query_Log_Analysis.md` — query volume, source, and field-level trend analysis |
| `/documents` | `Edit_Check_Specification.md` — programmed validation rules derived from the data dictionary<br>`Database_Lock_Readiness_Checklist.md` — lock-readiness sign-off checklist applied to this dataset |
| `/screenshots` | Screenshots of the actual workbook — Dashboard, Chart Data, Demographics, Adverse Events, Drug Accountability, and Query Log sheets |

## Screenshots

**Study Dashboard**

![Dashboard](screenshots/Dashboard.png)

**Chart Data**

![Chart Data](screenshots/Chart_Data.png)

**Source data — sample views**

*Demographics*
![Demographics](screenshots/Demographics.png)

*Adverse Events*
![Adverse Events](screenshots/Adverse_Events.png)

*Drug Accountability*
![Drug Accountability](screenshots/Drug_Accountability.png)

*Query Log*
![Query Log](screenshots/Query_Log.png)

---

## Study snapshot

- **Enrollment:** 100 subjects across 2 sites (ABC Medical College Hospital, Chennai; XYZ Multispeciality Hospital, Bengaluru) — 50/50 split, balanced by arm
- **Disposition:** 90 completed, 10 withdrawn (Consent, Lost to Follow-up, Lack of Efficacy, Protocol Deviation, AE, Worsening Renal Function)
- **Safety:** 63 adverse events logged — 62 non-serious / 1 serious; 40 mild, 16 moderate, 7 severe; 55 resolved, 7 ongoing, 1 led to withdrawal
- **Protocol deviations:** 16 logged across 6 categories (Informed Consent, Inclusion/Exclusion, Concomitant Medication, Dosing, Lab Sample, Visit Window)
- **Queries:** 28 raised, 28 resolved (100% resolution rate) across 9 fields
- **Drug accountability:** 100/100 subjects reconciled clean (Dispensed − Returned = Taken, verified)

## Skills demonstrated

`Cross-form data reconciliation` · `Query management & root-cause analysis` · `Edit check / validation rule design` · `Protocol deviation classification` · `Drug accountability review` · `Database lock readiness` · `Excel (formulas, INDEX/MATCH, data validation)` · `GCP-aligned documentation practices`

## Tools used

Microsoft Excel (source data), Python/pandas (automated cross-checks), Markdown (reporting)

---
*This is a training/demo project built on synthetic data for job-search portfolio purposes. It does not represent a real clinical trial or real patient information.*
