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
| Conversion differs by preferred language? | **See validation note below** | The original chi-square calculation needs correction before its p-value is reported |
| Time on new page differs by language? | Notebook concludes no statistically significant difference | See notebook for ANOVA details |

These results describe the **sample experiment**, not measured production uplift after a rollout.

## Recommendations
- Roll out the redesigned page in a controlled manner and monitor conversion and engagement.
- Continue multilingual support for English, French and Spanish.
- Test headlines, calls to action and layouts to seek further improvements.
- Investigate additional conversion drivers such as device type and traffic source.

## Repository contents
- [`ENews_Express_Analysis.ipynb`](ENews_Express_Analysis.ipynb): Original analysis, code, visualizations and conclusions
- `requirements.txt`: Python package dependencies

## Reproducing the analysis
The original notebook reads `abtest.csv` from a Google Drive path. **The dataset is not included** in this repository package. To rerun the analysis, obtain a dataset you are authorized to share/use and update the notebook's data-loading path. Notebook outputs are retained for review.

## Validation note before publication
The original notebook constructs the conversion-by-language contingency table with `margins=True` and passes that table to `chi2_contingency`. This includes a totals row and column in the statistical test and **is not the correct independence test**. Recompute using `pd.crosstab(df['language_preferred'], df['converted'])` (without margins), and update the corresponding conclusion before presenting that p-value publicly. The original notebook is preserved without silently changing its work. Also review embedded images, external links, dataset permissions and notebook outputs before making the repository public.

## Context
This is a data science learning project, presented as a portfolio case study; recommendations are analytical proposals, not claims of real-world implementation.
