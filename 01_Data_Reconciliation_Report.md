# Data Reconciliation Report
**Study:** Mock Phase II T2DM Trial (Drug X vs. Standard Therapy)
**Prepared by:** [Your Name] | **Role:** Clinical Data Management (portfolio project)
**Data cut:** Full dataset, 100 subjects / 700 visit records

## 1. Purpose

Cross-form reconciliation is a core CDM task: numbers reported on one form (e.g., a visit page flag) must agree with the detail captured on the source form (e.g., the Adverse Event log). This report documents the checks I ran against this dataset and the results, in the same style used for interim/final database lock review.

## 2. Checks performed and results

| # | Check | Method | Result |
|---|---|---|---|
| 1 | **AE cross-form reconciliation** — every visit flagged `AE Reported = Y` must have a matching record in the Adverse Events log | Matched `Subject ID` between Visits and Adverse_Events for all `AE Reported = Y` rows | ✅ 0 discrepancies — all AE flags trace to a logged AE |
| 2 | **Concomitant medication reconciliation** — every visit flagged `ConMed Reported = Y` must have a matching Concomitant Medications record | Matched `Subject ID` between Visits and Concomitant_Medications | ✅ 0 discrepancies |
| 3 | **Drug accountability arithmetic** — Total Dispensed − Total Returned should equal Total Taken, per subject | Recalculated for all 100 subjects and compared to the reported `Total Taken Tablets` | ✅ 0 discrepancies — all 100 subjects reconcile; Reconciliation Flag = "OK" for 100/100 |
| 4 | **Visit completeness** — every subject should have exactly 7 visit rows (Screening, Baseline, Visit 2–5, End of Study) | Row count per `Subject ID` in Visits | ✅ 700/700 expected rows present (100 × 7) |
| 5 | **Chronology check** — no visit date should precede the subject's enrollment date | Compared `Visit Date` to `Enrollment Date` per subject | ✅ 0 discrepancies |
| 6 | **Range checks — key labs/vitals** — HbA1c (4–16%), SBP (70–220 mmHg), DBP (40–140 mmHg) plausibility bounds | Flagged any value outside clinically plausible range | ✅ 0 out-of-range values found |

## 3. Interpretation

A 100% pass rate across these six checks indicates the dataset is internally consistent and ready for the next stage of review (e.g., SAE reconciliation with safety database, SDV against source, or database lock sign-off). In a live trial, this is the point at which a Data Manager would document the checks in the **Database Lock Readiness Checklist** (see `/documents`) rather than raise new queries — since no discrepancies were found here.

## 4. What this demonstrates

- Ability to design and execute **cross-form logic checks** (not just single-field range checks)
- Understanding of which relationships between CRF/eCRF forms actually need reconciling (AE flag ↔ AE log, ConMed flag ↔ ConMed log, dispensing math)
- Comfort documenting a **clean result** clearly and professionally — knowing what "good" looks like is as important as finding what's wrong
