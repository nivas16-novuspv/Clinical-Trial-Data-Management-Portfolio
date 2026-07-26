# Edit Check Specification
**Study:** Mock Phase II T2DM Trial | **Prepared by:** [Your Name], Clinical Data Management

## 1. Purpose

An Edit Check Specification defines the validation rules programmed into (or run against) study data to catch discrepancies automatically — before they require a manual query. This document translates the study's Data Dictionary into a set of testable rules, in the format typically reviewed and signed off by Data Management and Biostatistics during UAT (User Acceptance Testing) of an EDC build.

## 2. Range checks (single-field)

| Check ID | Form / Field | Rule | Query text if triggered |
|---|---|---|---|
| EC-01 | Demographics – Age | Must be 25–75 (protocol inclusion range) | "Age is outside the protocol-specified inclusion range (25–75). Please confirm." |
| EC-02 | Demographics – HbA1c_Baseline | Must be 7.0–10.5% (protocol inclusion range) | "Baseline HbA1c is outside the protocol range (7.0–10.5%). Please confirm source document." |
| EC-03 | Demographics – BMI_Baseline | Must be 25–40 kg/m² (protocol inclusion range) | "Baseline BMI is outside the protocol range (25–40). Please confirm height/weight entry." |
| EC-04 | Visits – SBP | Must be 70–220 mmHg | "SBP value implausible. Please verify against source." |
| EC-05 | Visits – DBP | Must be 40–140 mmHg | "DBP value implausible. Please verify against source." |
| EC-06 | Visits – Compliance_Percent | Must be 0–100 | "Compliance percent exceeds 100%. Please verify tablet counts." |
| EC-07 | Visits – Temperature_C | Must be 35.0–40.0°C | "Temperature value implausible. Please verify units (°C vs °F) and source." |

## 3. Cross-field / cross-form checks (logic checks)

| Check ID | Forms involved | Rule | Rationale |
|---|---|---|---|
| EC-08 | Visits.AE_Reported ↔ Adverse_Events | If `AE_Reported = Y` on a visit, a matching record must exist in Adverse_Events for that subject | Prevents under-reporting of safety data; this is the check run in `01_Data_Reconciliation_Report.md` |
| EC-09 | Visits.ConMed_Reported ↔ Concomitant_Medications | If `ConMed_Reported = Y`, a matching record must exist in Concomitant_Medications | Same logic as EC-08, applied to con meds |
| EC-10 | Drug_Accountability | `Total_Dispensed − Total_Returned = Total_Taken`; flag `DISCREPANCY` if Returned > Dispensed | Core drug accountability reconciliation — a GCP requirement |
| EC-11 | Visits.Visit_Date ↔ Demographics.Enrollment_Date | Visit_Date must not precede Enrollment_Date | Chronology check; catches transcription/date-entry errors |
| EC-12 | Visits.Visit_Date (sequential) | Visit_Date for Visit N must not precede Visit_Date for Visit N−1 | Catches out-of-sequence visit entry |
| EC-13 | Withdrawals ↔ Visits | If a subject has a Withdrawal record, all subsequent visits should be `Visit_Status = "Not Applicable - Withdrawn"` | Ensures disposition is reflected consistently across forms |

## 4. Severity classification

| Severity | Definition | Example |
|---|---|---|
| **Hard edit (blocking)** | Prevents form save/lock until resolved | EC-06 (Compliance >100%), EC-10 (accountability discrepancy) |
| **Soft edit (warning)** | Flags for review but does not block save | EC-01–EC-05, EC-07 (baseline eligibility ranges — may be a legitimate protocol deviation, not a data error) |
| **Manual/listing review** | Not programmable as a real-time check; reviewed periodically via listing | EC-11–EC-13 (chronology and disposition consistency) |

## 5. What this demonstrates

- Ability to read a protocol/data dictionary and translate eligibility criteria and expected data relationships into **testable rules**
- Understanding of the difference between a **hard edit, soft edit, and manual listing review** — a distinction tested in real CDM/EDC build UAT
- Applied result: when run against this dataset (see Reconciliation Report), all 100 subjects and 700 visit records pass every rule above, with the *design of the rules themselves* being the deliverable
