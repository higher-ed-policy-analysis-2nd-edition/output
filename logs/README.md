# Output Logs

**Repository:** `higher-ed-policy-analysis-2nd-edition / output`  
**Path:** [`output/logs`](https://github.com/higher-ed-policy-analysis-2nd-edition/output/tree/main/logs)  
**Book:** *Higher Education Policy Analysis Using Quantitative Techniques*, Second Edition — Springer

---

## Overview

This directory contains the full console output logs produced by running each chapter's analysis scripts. Every Stata script writes a plain-text `.log` file via `log using`; every R script captures console output via `sink()`. Logs are the authoritative record of what each script produced on the author's machine and serve three purposes: result verification (confirming that printed statistics in the chapter text match the live output), reproduction checking (confirming that a reader's run produces equivalent output), and debugging (isolating where a script diverges from expected output).

---

## Naming Convention

```
Chapter{N}_Stata_output.log    ← Stata log (all chapters)
Chapter{N}_R_output.log        ← R log (all chapters with an R translation)
```

Both file types are plain text and can be opened in any text editor. Stata logs are written with `log using ..., replace text`; R logs are captured with `sink(..., append = FALSE, split = TRUE)` so output is written to file and echoed to the console simultaneously.

---

## Files

### Chapter 4 — Creating and Managing Datasets

| File | Script |
|------|--------|
| `Chapter4_Stata_output.log` | [`code/ch4/Stata_code4.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch4/Stata_code4.do) |
| `Chapter4_R_output.log` | [`code/ch4/R_code4.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch4/R_code4.R) |

Log contents: dataset import and merge diagnostics, `describe` and `codebook` output, label summaries, `compress` before/after memory usage, and save confirmations.

---

### Chapter 5 — Missing Data Analysis

| File | Script |
|------|--------|
| `Chapter5_Stata_output.log` | [`code/ch5/Stata_code5.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch5/Stata_code5.do) |
| `Chapter5_R_output.log` | [`code/ch5/R_code5.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch5/R_code5.R) |

Log contents: `mdesc` and `misstable` output, `xtmispanel` module results (detect, test, graph), MCAR chi-squared and MAR logistic test statistics, missingness-by-panel-unit and missingness-by-fiscal-year tables, and mechanism classification.

---

### Chapter 6 — Descriptive Statistics and Data Visualization

| File | Script |
|------|--------|
| `Chapter6_Stata_output.log` | [`code/ch6/Stata_code6.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch6/Stata_code6.do) |
| `Chapter6_R_output.log` | [`code/ch6/R_code6.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch6/R_code6.R) |

Log contents: `tabstat`, `summarize`, and `correlate` output; `histogram` and `scatter` export confirmations; frequency tabulations.

---

### Chapter 7 — OLS, Fixed-Effects, and Random-Effects Regression

| File | Script |
|------|--------|
| `Chapter7_Stata_output.log` | [`code/ch7/Stata_code7.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch7/Stata_code7.do) |
| `Chapter7_R_output.log` | [`code/ch7/R_code7.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch7/R_code7.R) |

Log contents: pooled OLS, fixed-effects (`xtreg, fe`), and random-effects (`xtreg, re`) regression tables; Hausman test output; VIF diagnostics; `xtdescribe` panel structure summary.

---

### Chapter 8 — State Fiscal Dynamics: ARDL-ECM Analysis

| File | Script |
|------|--------|
| `Chapter8_Stata_output.log` | [`code/ch8/Stata_code8.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch8/Stata_code8.do) |
| `Chapter8_R_output.log` | [`code/ch8/R_code8.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch8/R_code8.R) |

Log contents: panel unit root test results (`xtpurt`), Kao/Pedroni/Westerlund cointegration test output, cross-sectional dependence (`xtcdf`) and slope homogeneity (`xthst`) test statistics, asymmetric ARDL-ECM coefficient tables (NARDL with partial sum decomposition), mean group (MG) estimates via `statsby`, short-run symmetry test, and ECM speed-of-adjustment coefficients. Key finding logged: short-run symmetry but long-run ratchet effect.

---

### Chapter 9 — Advanced Panel Time-Series Methods

| File | Script |
|------|--------|
| `Chapter9_Stata_output.log` | [`code/ch9/Stata_code9.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch9/Stata_code9.do) |
| `Chapter9_R_output.log` | [`code/ch9/R_code9.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch9/R_code9.R) |

Log contents: DCCE-MG and CS-PQARDL estimation output (`xtdcce2`), cross-sectional dependence and homogeneity test results, quantile-specific long-run coefficients across τ = 0.10–0.90, sub-period analysis results, and figure export confirmations. Data source: SHEEO state appropriations panel, FY 1980–2024.

---

### Chapter 10 — Causal Inference Methods and MTE

| File | Script |
|------|--------|
| `Chapter10_Stata_output.log` | [`code/ch10/Stata_code10.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch10/Stata_code10.do) |
| `Chapter10_R_output.log` | [`code/ch10/R_code10.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch10/R_code10.R) |

Log contents: TWFE DiD coefficient tables, LASSO-residualized DiD output, synthetic control method (SCM) results and RMSPE, synthetic DiD (SDiD) estimates, Callaway–Sant'Anna staggered adoption results, probit first-stage output (F-statistic, GA funding coefficient), cubic MTE polynomial coefficient table, ATE/ATT/ATU estimates, field-specific ATE differentials (Table 10.1), MPRTE results by policy scenario (Table 10.2), and parametric bootstrap progress indicators. Data source: Georgia higher education consolidation panel and B&B-mirroring synthetic dataset.

---

### Chapter 11 — Bayesian MTE Microsimulation

| File | Script |
|------|--------|
| `Chapter11_Stata_output.log` | [`code/ch11/Stata_code11.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch11/Stata_code11.do) |
| `Chapter11_R_output.log` | [`code/ch11/R_code11.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch11/R_code11.R) |

Log contents: synthetic dataset generation confirmation, policy exposure summary (`tabstat` on `grad_plus_loans`; cap-affected student counts by program area), probit first-stage F-statistic and GA funding coefficient, cubic MTE polynomial estimates, ATE/ATT/ATU point estimates, point-estimate CBA components (fiscal savings, behavioral cost, efficiency gain, institutional revenue loss), Bayesian simulation progress indicators (every 100 draws), posterior summary statistics with 95% credible intervals for all CBA components, P(NB > 0) and P(Extended NB > 0), benefit-cost ratio posterior distribution, and figure export confirmations for Figs. 11.1–11.7.

---

### Chapter 12 — Simulation-Based Methods: Free Community College CBA

| File | Script |
|------|--------|
| `Chapter12_Stata_output.log` | [`code/ch12/Stata_code12.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch12/Stata_code12.do) |
| `Chapter12_R_output.log` | [`code/ch12/R_code12.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch12/R_code12.R) |

Log contents: 50-state × 15–25-year synthetic panel construction, CCE-TWFE and DCCE-MG estimates, Callaway–Sant'Anna staggered adoption results, synthetic DiD output, IPTW dose-response estimates, Rambachan–Roth sensitivity analysis, placebo test results, Bayesian CBA loop progress indicators, posterior BCR distribution summary (E[BCR] ≈ 0.40–0.50), P(BCR > 1), infra-marginal transfer share (η ≈ 11%), and last-dollar BCR.

---

## Log Structure

All Stata logs follow this internal structure:

```
Log file: <working_directory>/Output/logs/Chapter{N}_Stata_output.log
Chapter {N} log opened: <date> <time>
============================================================
  Section 1: ...
============================================================
[section output]
...
============================================================
  Chapter {N} Script Complete
============================================================
Output files:
  Stata log:    Output/logs/Chapter{N}_Stata_output.log
  ...
```

All R logs follow this structure:

```
============================================================
Chapter {N} R Log Opened: <timestamp>
============================================================

Section 2: ...
[section output]
...
Chapter {N} R Script Complete.
```

---

## Reproduction

To regenerate a log, run the corresponding script from the `code/ch{N}` directory. Log files are opened with `replace` (Stata) and `append = FALSE` (R), so each run overwrites the previous log. The working directory must be set to the chapter folder before running.

All scripts and their requirements are documented in the `code` repository:  
[`code/`](https://github.com/higher-ed-policy-analysis-2nd-edition/code)

---

## Citation

> Titus, M. A. (forthcoming). *Higher Education Policy Analysis Using Quantitative Techniques* (2nd ed.). Springer.

Code development was assisted by Claude (Anthropic, 2025). The author provided all methodological specifications and reviewed, tested, and validated all code and output.
