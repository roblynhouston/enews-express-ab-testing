# E-News Express | A/B Testing & Conversion Analysis

**Portfolio case study · Statistical experimentation · Python**

## Executive summary
E-News Express wanted to determine whether a redesigned landing page could increase engagement and subscriber conversions. In this educational case study, I analyzed an experiment with **100 users**, split equally between the existing page (control) and redesigned page (treatment), using exploratory analysis and statistical hypothesis tests at a **5% significance level**.

**Primary finding:** The notebook reports statistically significant improvements in time spent on the redesigned page and subscriber conversion. I recommended rolling out the redesign while continuing to test page elements and monitor results.

## Business questions
1. Do visitors spend more time on the redesigned landing page?
2. Is the new page's conversion rate higher?
3. Is conversion associated with language preference?
4. Does time spent on the new page vary across language groups?

## Data and methods
- **Observations:** 100 users; 50 control and 50 treatment
- **Fields:** user ID, experimental group, landing page, time spent, converted, preferred language
- **Tools:** Python, pandas, NumPy, SciPy, statsmodels, Matplotlib, Seaborn
- **Methods:** Data quality checks, univariate and bivariate EDA, one-sided Welch t-test, two-proportion z-test, chi-square independence test, ANOVA and assumption checks

## Selected findings from the original notebook
| Question | Notebook result | Interpretation |
|---|---|---|
| More time on new page? | One-sided t-test **p = 0.000139** | Statistically significant evidence of greater engagement |
| Higher conversion on new page? | One-sided two-proportion z-test **p = 0.00803** | Statistically significant evidence of higher conversion |
| Conversion differs by preferred language? | **Corrected p = 0.2130** | No statistically significant association detected at α = 0.05 |
| Time on new page differs by language? | Notebook concludes no statistically significant difference | See notebook for ANOVA details |

These results describe the **sample experiment**, not measured production uplift after a rollout.

## Recommendations
- Roll out the redesigned page in a controlled manner and monitor conversion and engagement.
- Continue multilingual support for English, French and Spanish.
- Test headlines, calls to action and layouts to seek further improvements.
- Investigate additional conversion drivers such as device type and traffic source.

## Repository contents
- [`ENews_Express_Analysis.ipynb`](ENews_Express_Analysis.ipynb): Analysis, code, visualizations and corrected chi-square test
- `requirements.txt`: Python package dependencies
- `abtest.csv`: Educational project dataset (100 observations)

## Reproducing the analysis
1. Download the notebook, `abtest.csv`, and `requirements.txt` into the same folder.
2. Install packages using `pip install -r requirements.txt`.
3. Open the notebook in Jupyter and run all cells in order. If using Google Colab, upload `abtest.csv` into the session first.

## Statistical validation
The original chi-square calculation included contingency-table totals, which are not valid inputs for the test. The notebook now uses the observed 3 × 2 table without margins. **Corrected χ² = 3.0930, df = 2, p = 0.2130.** At α = 0.05, we fail to reject independence; there is insufficient evidence of an association between language preference and conversion. This is not proof of independence. The original analysis otherwise remains intact; rerun the notebook to refresh any saved outputs.

## Context
This is a data science learning project, presented as a portfolio case study; recommendations are analytical proposals, not claims of real-world implementation.
