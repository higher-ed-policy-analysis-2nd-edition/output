# Chapter 11 Figures: Bayesian MTE Microsimulation

**Repository:** `higher-ed-policy-analysis-2nd-edition / output`  
**Path:** [`output/graphs/ch11`](https://github.com/higher-ed-policy-analysis-2nd-edition/output/tree/main/graphs/ch11)  
**Book:** *Higher Education Policy Analysis Using Quantitative Techniques*, Second Edition — Springer

---

## Overview

This directory contains the seven figures produced in **Chapter 11: Bayesian MTE Microsimulation — Cost–Benefit Analysis of a \$100k Lifetime Cap on Grad PLUS Loans**. Each figure is provided in two versions: a Stata-generated file (`_Stata.png`) and an R-generated equivalent (`_R.png`). Both versions are exported in grayscale at 1,200-pixel width to meet Springer print standards.

Figures are grouped into three thematic sets: posterior distributions and CBA decomposition (Figs. 11.1–11.3), treatment effect heterogeneity (Figs. 11.4–11.5), and institutional revenue impacts (Figs. 11.6–11.7).

---

## Files

| Figure | Stata file | R file |
|--------|-----------|--------|
| Fig. 11.1 | `fig11_1_posterior_nb_Stata.png` | `fig11_1_posterior_nb_R.png` |
| Fig. 11.2 | `fig11_2_mte_policy_Stata.png` | `fig11_2_mte_policy_R.png` |
| Fig. 11.3 | `fig11_3_cba_decomp_Stata.png` | `fig11_3_cba_decomp_R.png` |
| Fig. 11.4 | `fig11_4_param_posteriors_Stata.png` | `fig11_4_param_posteriors_R.png` |
| Fig. 11.5 | `fig11_5_mte_byfield_Stata.png` | `fig11_5_mte_byfield_R.png` |
| Fig. 11.6 | `fig11_6_inst_rev_byfield_Stata.png` | `fig11_6_inst_rev_byfield_R.png` |
| Fig. 11.7 | `fig11_7_full_cost_stack_Stata.png` | `fig11_7_full_cost_stack_R.png` |

---

## Figure Descriptions

### Fig. 11.1 — Posterior Distribution of Net Social Benefits

Histogram of the net social benefit (\$000s) across 1,000 Bayesian posterior draws. A dashed vertical line marks zero; a solid vertical line marks the posterior mean. The distribution illustrates the full range of outcomes the estimated model supports, communicating both the central tendency and the spread of the simulation's welfare verdict. Percent of posterior draws is shown on the y-axis.

**Data source:** `Output/tables/sim_results_ch11.dta` (variable: `net_benefit_s`)  
**Stata section:** Section 10 — Fig. 11.1 block  
**R section:** Section 10, `ggplot` histogram block

---

### Fig. 11.2 — MTE Curve with Policy-Affected Margin

Line plot of the estimated MTE as a function of *u* (unobserved resistance to treatment, ranging from 0 to 1), computed from the posterior mean of the cubic polynomial coefficients (b0, b1, b2, b3) across all 1,000 draws. The policy-affected region (*u* ∈ [0.30, 0.65]) is shaded in two colors: dark gray where MTE > 0 (behavioral cost area — displaced students with positive returns) and light gray where MTE ≤ 0 (efficiency gain area — displaced students with below-zero returns). A dashed horizontal line marks MTE = 0.

**Data source:** Posterior mean coefficients from `sim_results_ch11.dta`; 100-point grid in *u*  
**Stata section:** Section 10 — Fig. 11.2 block  
**R section:** Section 10, `plot_df` construction and `ggplot` line/area block

---

### Fig. 11.3 — Cost–Benefit Decomposition

Bar chart showing the posterior mean of each CBA component: fiscal savings (positive), efficiency gain (positive), and behavioral cost (shown as negative). The figure provides a visual summary of the scale disparity between the policy's benefits and its costs, with the behavioral cost bar dwarfing the two benefit bars by approximately an order of magnitude.

**Data source:** Posterior means of `fiscal_s`, `effic_gain_s`, `behav_cost_s` from `sim_results_ch11.dta`  
**Stata section:** Section 10 — Fig. 11.3 block  
**R section:** Section 10, `summary_stats` pivot and `ggplot` bar block

---

### Fig. 11.4 — Posterior Distributions of ATE, ATT, and ATU

Overlapping kernel density plots of the posterior distributions of the average treatment effect (ATE), average treatment effect on the treated (ATT), and average treatment effect on the untreated (ATU) across all 1,000 draws. Three distinct line patterns (solid, dashed, short-dash) distinguish the parameters without requiring color. The figure illustrates both the ATU > ATT > ATE ordering — reflecting negative selection on gains — and the relative posterior uncertainty of each parameter, with ATE showing the widest spread and ATT and ATU more tightly estimated.

**Data source:** Variables `ate_s`, `att_s`, `atu_s` from `sim_results_ch11.dta`  
**Stata section:** Section 10 — Fig. 11.4 block (`kdensity`-based)  
**R section:** Section 10, `pivot_longer` and `geom_density` block

---

### Fig. 11.5 — MTE Curves by Graduate Program Area

Five MTE curves displayed on the same axes, one for each graduate program area: Business, STEM, Health, Education, and Other (base category). The curves are constructed by applying program-area ATE differentials from Chapter 10 (Table 10.1) as parallel vertical shifts of the pooled posterior-mean cubic MTE curve. Five distinct line patterns distinguish the fields. The figure illustrates that the general shape of heterogeneous returns is consistent across fields but that Business programs carry the largest returns and Education the smallest, with corresponding implications for which fields bear the heaviest human capital cost if the cap displaces students.

**Field offsets (from Chapter 10, Table 10.1):**

| Field | ATE offset |
|-------|-----------|
| Business | +0.885 |
| STEM | +0.134 |
| Health | +0.038 |
| Education | −0.165 |
| Other | 0 (base) |

**Data source:** Point-estimate polynomial coefficients from Section 5; 100-point *u* grid  
**Stata section:** Section 10 — Fig. 11.5 block  
**R section:** Section 10, `plot_df_fields` pivot and `geom_line` block

---

### Fig. 11.6 — Institutional Revenue Loss by Program Area

Bar chart of total net institutional revenue loss (\$000s) aggregated by graduate program area (Business, STEM, Health, Education, Other), sorted in descending order of loss. Revenue loss is computed as the sum of `displaced_E × net_inst_rev` across cap-affected completers within each area, where `net_inst_rev` equals 65% of gross tuition per enrolled student. The figure shows that Business programs account for the largest share of institutional losses, driven by the combination of high tuition and high cap-exposure rates, while Education programs contribute the least.

**Data source:** `Example_11_1.dta` (collapsed to program-area level)  
**Stata section:** Section 10 — Fig. 11.6 block  
**R section:** Section 10, `inst_df` collapse and `ggplot` bar block

---

### Fig. 11.7 — Full Social Cost Stack

Five-bar chart stacking all cost and benefit components from both the student and institutional channels. Benefits (fiscal savings, efficiency gain) are shown as positive bars; costs (behavioral cost, institutional revenue loss, cross-subsidy disruption) are shown as negative bars. A dashed horizontal line marks zero. This is the chapter's most comprehensive summary visualization: it makes the complete cost structure legible at a glance and reinforces that the policy's costs exceed its benefits by more than an order of magnitude.

**Components:**

| Bar | Direction | Value source |
|-----|-----------|-------------|
| Fiscal Savings | Positive | Posterior mean of `fiscal_s` |
| Efficiency Gain | Positive | Posterior mean of `effic_gain_s` |
| Human Capital Loss | Negative | Posterior mean of `behav_cost_s` |
| Institutional Rev. Loss | Negative | Posterior mean of `inst_rev_loss_s` |
| Cross-Subsidy Disruption | Negative | 20% × `inst_rev_loss_s` |

**Data source:** Posterior means from `sim_results_ch11.dta`  
**Stata section:** Section 10 — Fig. 11.7 block  
**R section:** Section 10, `stack_data` construction and `geom_bar` block

---

## Reproduction

To reproduce all figures, run either analysis script from the `code/ch11` directory:

- **Stata:** [`code/ch11/Stata_code11.do`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch11/Stata_code11.do) (Stata 19+, no additional packages)
- **R:** [`code/ch11/R_code11.R`](https://github.com/higher-ed-policy-analysis-2nd-edition/code/blob/main/ch11/R_code11.R) (R 4.4+; packages: `tidyverse`, `fixest`, `MASS`, `scales`, `broom`)

The input dataset is [`data/ch11/Example_11_1.dta`](https://github.com/higher-ed-policy-analysis-2nd-edition/data/tree/main/ch11). Both scripts generate the dataset synthetically if it is not found locally and attempt a remote download from the data repository before falling back to generation.

Figures are written to `Output/graphs/` relative to the working directory set in each script. The random seed is `20251201` in both scripts; Stata and R produce distributional equivalents rather than row-identical figures due to differences in their pseudo-random number generators.

---

## Technical Specifications

| Property | Value |
|----------|-------|
| Format | PNG |
| Width | 1,200 px (Stata); 8–9 in at screen resolution (R) |
| Color scheme | Grayscale (Springer print standard) |
| Stata scheme | `s2mono` (monochrome) |
| R theme | `theme_minimal()` with gray fill palette |
| Random seed | `20251201` |
| Posterior draws | S = 1,000 |

---

## Citation

> Titus, M. A. (forthcoming). *Higher Education Policy Analysis Using Quantitative Techniques* (2nd ed.). Springer.

Code development was assisted by Claude (Anthropic, 2025). The author provided all methodological specifications and reviewed, tested, and validated all code and output.
