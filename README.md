# MIDUS 3: Sex Differences in Cognitive Test Performance

**Reproducible statistical analysis of episodic memory, executive functioning, and between-person variability** using two public-use datasets from the Midlife in the United States (MIDUS 3) research program.

**Research status:** Working research project / manuscript in preparation. **Not peer-reviewed.** The findings describe associations in a selected U.S. longitudinal cohort, not causal or innate sex differences, IQ, or nationally representative estimates.

## Research question

How do male and female participants in MIDUS 3 differ in mean episodic-memory and executive-functioning scores, within-sex variability, and score distributions? Our two co-primary outcomes are BTACT episodic memory (`C3TEM`) and executive functioning (`C3TEF`).

## Headline findings

Age-adjusted, family-clustered analyses of the original MIDUS 3 cohort found:

| Outcome | Analytic N | Male − female adjusted mean difference | Nominal 95% CI | Adjusted residual variance ratio M/F (95% family-bootstrap CI) |
| --- | ---: | ---: | --- | --- |
| Episodic memory | 2,687 | −0.473 | [−0.540, −0.406] | 0.667 [0.595, 0.750] |
| Executive functioning | 2,408 | +0.142 | [0.091, 0.193] | 1.279 [1.130, 1.444] |

The two mean comparisons are the confirmatory family, evaluated with Holm correction. Variance ratios, quantile/tail analyses, and equivalence tests are exploratory. The executive-functioning analytic sample applies the study-recommended clean SGST filter. See the [notebook](notebooks/MIDUS3_Final_Complete_Analysis.ipynb) for full definitions, uncertainty calculations, filtering, and sensitivity analyses.

**Important:** These are preliminary analytic estimates; quality-flag sensitivity checks, measurement boundaries (including word-recall floor effects), age approximation, selection/attrition, and the justification for exploratory equivalence bounds remain relevant to journal preparation. The unadjusted Hedges' g is not the age-adjusted regression coefficient.

## Reproduce the analysis in Google Colab

1. Download the two official ICPSR **Stata-format ZIP files** directly from their pages (registration / terms of use may apply):
   - [ICPSR 37095, version 3: MIDUS 3 Cognitive Project (2013–2017)](https://doi.org/10.3886/ICPSR37095.v3) → save as `ICPSR_37095-V3.zip`.
   - [ICPSR 36346, version 7: MIDUS 3 Survey Project 1 (2013–2014)](https://doi.org/10.3886/ICPSR36346.v7) → save as `ICPSR_36346-V7.zip`.
2. Open [`notebooks/MIDUS3_Final_Complete_Analysis.ipynb`](notebooks/MIDUS3_Final_Complete_Analysis.ipynb) in [Google Colab](https://colab.research.google.com/), upload those two ZIP files in the file pane, and select **Runtime → Run all**.
3. The notebook validates the archives and writes aggregate CSVs/PNG figures to its generated `MIDUS3_final_results/` directory.

No supplementary `.py` script is required. The analysis uses Python, NumPy, pandas, SciPy, statsmodels and Matplotlib; see [`requirements.txt`](requirements.txt). Its random seed is `20261030`. Bootstrap is performed at the family level (2,000 repetitions for primary variance-ratio intervals and Hedges' g uncertainty).

> **Data policy:** Original ICPSR microdata are **not included** in this repository. Access them from the distributors and follow their conditions. Do not commit dataset archives, extracted `.dta` files, or respondent-level exports. A `.gitignore` is provided to prevent accidental uploads.

## Repository layout

```text
notebooks/  Final reproducible analysis notebook (outputs cleared for sharing)
results/    Aggregate-only CSV tables and the textual summary
figures/    Figures generated from aggregate analyses
data/       Instructions for obtaining the original datasets (not the datasets)
```

## Design and limitations

- Cross-sectional comparison within a longitudinal cohort; the primary restriction is the original MIDUS 3 cohort rather than the Milwaukee or Refielding components.
- Sex is the binary recorded study variable; sex and sociocultural gender are not assumed to be interchangeable.
- Primary outcome-specific OLS models adjust for centered approximate age at cognitive testing and age squared, with family-clustered standard errors; Holm adjustment controls the two primary tests.
- Family-bootstrap CIs for ratios of age-adjusted residual variances are constructed on the log scale.
- Secondary analyses examine education, sample composition, task-quality restrictions, quantiles, empirical distributions, tail proportions and exploratory equivalence tests.
- Age at testing is approximated from survey age and elapsed interview months. Results are unweighted; selective survival, attrition, and measurement ceilings/floors limit generalizability.

## Scientific context

This project builds on earlier MIDUS mean comparisons (e.g., Hughes et al., 2018) and distinguishes between-person variability from within-person cognitive dispersion. It does **not** claim to be the first study of sex-related cognitive differences or variability.

- Hughes et al. (2018): [DOI](https://doi.org/10.1017/S1355617718000425)
- Asperholm et al. (2020): [DOI](https://doi.org/10.3389/fpsyg.2020.00613)
- Full bibliography and scientific discussion will accompany the manuscript after further review.

## Data citations

- Ryff, C. D., & Lachman, M. E. (2023). *Midlife in the United States (MIDUS 3): Cognitive Project, 2013–2017* (ICPSR 37095, v3). ICPSR. https://doi.org/10.3886/ICPSR37095.v3
- Ryff, C., et al. (2019). *Midlife in the United States (MIDUS 3), 2013–2014* (ICPSR 36346, v7). ICPSR. https://doi.org/10.3886/ICPSR36346.v7

## Authorship and citation

Research and analysis: **Nurmukhammet Toigonbekov**, Ala-Too International University (MATDAIS-25). See [`CITATION.cff`](CITATION.cff) for a machine-readable software citation.

This GitHub release is a code-and-results repository, **not** a journal publication or peer-reviewed preprint. No software license has been chosen yet; please contact the author before reusing beyond applicable law.