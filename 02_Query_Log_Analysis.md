# Query Log Analysis
**Study:** Mock Phase II T2DM Trial | **Source:** `Query_Log` sheet (28 queries, 100% resolved)

## 1. Purpose

Query trend analysis helps a Data Manager spot systemic issues — e.g., one site consistently mis-entering a field, or one CRF field that's poorly designed and generates repeat queries. This is standard input into a mid-study **Data Management Report** shared with the study team.

## 2. Query volume by field

| Field | Queries | % of total |
|---|---|---|
| SBP | 6 | 21% |
| Visit_Date | 5 | 18% |
| Weight_kg | 4 | 14% |
| AE_Reported | 4 | 14% |
| Compliance_Percent | 3 | 11% |
| Creatinine_mgdL | 2 | 7% |
| AST_UL | 2 | 7% |
| HbA1c | 1 | 4% |
| Hemoglobin_gdL | 1 | 4% |

**Observation:** `SBP` and `Visit_Date` together account for ~39% of all queries. In a real study, this pattern would prompt a recommendation: re-train sites on blood pressure entry (units/transcription) and tighten the visit date edit check window (see `Edit_Check_Specification.md`), since date and vitals entry errors are typically preventable with better field-level guidance or an earlier real-time edit check.

## 3. Query source (who raised it)

| Raised By | Queries | % of total |
|---|---|---|
| CRC (site coordinator) | 12 | 43% |
| CRA (monitor) | 10 | 36% |
| Data Manager | 6 | 21% |

**Observation:** Most queries originate at the site level (CRC) or during monitoring visits (CRA), consistent with a healthy query workflow — issues are being caught close to source rather than only surfacing at final DM review.

## 4. Resolution status

- **28 of 28 queries resolved (100%)** — no open queries remain at this data cut.
- This is the metric reported on a study's **Query Management Dashboard** ahead of database lock; a 100% resolution rate with no aging queries >30 days is a green flag for lock readiness.

## 5. What this demonstrates

- Ability to turn a raw query log into **actionable trend analysis**, not just a status list
- Understanding of the query lifecycle (site → CRA → DM → resolution) and who typically raises what
- Translating findings into a **process recommendation** (site retraining, edit check tuning) — the part that shows you think like a Data Manager, not just a data entry checker
