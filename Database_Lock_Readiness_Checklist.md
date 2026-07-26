# Database Lock Readiness Checklist
**Study:** Mock Phase II T2DM Trial | **Applied by:** [Your Name], Clinical Data Management
**Purpose:** Standard sign-off checklist a Data Manager completes before recommending database lock. Applied here against the full 100-subject dataset.

| # | Item | Status | Evidence |
|---|---|---|---|
| 1 | All expected visits accounted for (no missing CRF pages) | ✅ Pass | 700/700 expected visit rows present |
| 2 | All open queries resolved | ✅ Pass | 28/28 queries resolved (0 open) — see `Query_Log_Analysis.md` |
| 3 | AE log reconciled against visit-level AE flags | ✅ Pass | 0 discrepancies — see `01_Data_Reconciliation_Report.md` §2.1 |
| 4 | Concomitant medication log reconciled against visit-level ConMed flags | ✅ Pass | 0 discrepancies — see `01_Data_Reconciliation_Report.md` §2.2 |
| 5 | Drug accountability reconciled for all subjects | ✅ Pass | 100/100 subjects, Reconciliation Flag = "OK" |
| 6 | Serious Adverse Events (SAEs) reviewed and outcome documented | ✅ Pass | 1 SAE identified, outcome = Resolved |
| 7 | Protocol deviations reviewed and classified | ✅ Pass | 16 deviations logged across 6 categories, each with corrective action documented |
| 8 | Withdrawal disposition consistent with visit records | ✅ Pass | 10 withdrawals; reasons documented (Consent, LTFU, Efficacy, Deviation, AE, Renal) |
| 9 | No out-of-range values on key safety/efficacy labs (HbA1c, SBP/DBP) | ✅ Pass | 0 out-of-range values across 700 visit records |
| 10 | Randomization balance confirmed (arm, site) | ✅ Pass | 50/50 by arm; 50/50 by site |

## Recommendation

Based on the checks above, this dataset meets the standard criteria for **database lock readiness**. In a live study this checklist would be co-signed by the Lead Data Manager, Biostatistician, and Medical Monitor before the lock is executed and the database is finalized for analysis.

## What this demonstrates

- Familiarity with the **end-to-end CDM workflow**, from edit checks → query resolution → reconciliation → lock sign-off
- Ability to synthesize multiple reports into a single, decision-ready checklist — the kind of document a study lead actually reads
