# Final QA Report — Oilfield Production & Data Quality Analysis

**Project:** Excel & Power Query Portfolio Project  
**Reporting period:** May 1–30, 2026  
**Dataset:** Simulated oilfield production data (six wells)  
**Review date:** November 12, 2026  
**Evidence basis:** Workbook screenshots and QA outcomes reported during project exercises; not an independent audit of the full workbook file.

## 1. QA Scope

This report summarizes checks performed on the production dashboard, Power Query transformations, and data quality reporting. It distinguishes successful processing and reconciliation from unresolved source-data defects.

## 2. Results

| Test | Outcome | Evidence / qualification |
|---|---|---|
| KPI reconciliation | Passed (reported) | Dashboard values matched exercise results after refresh. |
| Data quality audit | Passed (reported) | Missing and duplicate Date–Well combinations and invalid values were documented. |
| Power Query parameter | Passed | `pCSVFilePath` was created and used in `File.Contents(pCSVFilePath)`; preview showed 183 rows and six source columns. |
| Query refresh | Passed for visible queries | Screenshots showed loaded rows for `Dashboard_Data` (183), `Data_Query_Validation` (183), `Actual_Date_Well` (179), `Expected_Date_Well` (180), and `Missing_Date_Well` (1). Other queries were not individually verified in the screenshots. |
| Dashboard KPI consistency | Passed (reported) | Reported production 128,825.1 bbl; 183 records; 97.81% value validation pass rate; four records requiring review. |
| Cross-computer reproducibility | Not tested | A different computer must set `pCSVFilePath` to its own local CSV path before refresh. |
| Source-data issue resolution | Pending | Missing, duplicate, conflicting, and invalid records require authoritative source verification. |

## 3. Reconciled Dashboard Metrics

| Metric | Reported result |
|---|---:|
| Total reported oil production | 128,825.1 bbl |
| Total source records | 183 |
| Value-validation passing records | 179 |
| Records requiring value review | 4 |
| Value-validation pass rate | 97.81% |
| Highest-producing well | W-103 — 32,256.7 bbl |
| Lowest-producing well | W-105 — 12,001.7 bbl |
| Highest reported daily production | May 3 — 6,110.6 bbl |
| Lowest reported daily production | May 7 — 2,496.0 bbl |

**Interpretation:** The 97.81% pass rate evaluates oil and downtime value checks only; it does not certify uniqueness or reporting completeness. All production totals remain provisional.

## 4. Outstanding Data Quality Findings

- One expected Date–Well combination is missing: W-106 on May 11, 2026.
- Four extra records occur across four duplicated Date–Well combinations: two exact duplicate pairs and two conflicting duplicate pairs.
- One negative oil production value (−25 bbl), one downtime value above 24 hours (26 hr), and missing oil and downtime values require review.
- The issue log contains the recommended follow-up for each finding; no unsupported corrections were applied.

## 5. Refresh Instructions

1. Download the workbook and source CSV into a local folder.
2. Open the workbook in Excel with Power Query support.
3. Go to **Data → Queries & Connections**, edit the source query, and open **Manage Parameters**.
4. Set `pCSVFilePath` to the CSV's full local file path.
5. Choose **Close & Load**, then **Data → Refresh All**.
6. Verify that the dashboard shows the expected KPIs and inspect query refresh errors if any occur.

## 6. Release Assessment

**Portfolio publication: suitable with explicit limitations.** The dashboard and refresh were tested using the existing source environment. The workbook is not certified as fully portable to other computers, and source-level data issues are unresolved. This is an educational project using simulated data, not an operational production report.
