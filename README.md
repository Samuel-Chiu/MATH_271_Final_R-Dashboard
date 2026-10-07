# MATH 271 Final: Customer Personality Analysis

Multivariate analysis (bootstrapping, PCA, and redundancy analysis) of a retail customer dataset, presented as a tabbed R Markdown report.

Final project for **MATH 271** at UH Hilo (Spring 2024), the final course in the R portion of the Data Science certificate.

<!-- screenshot: rendered report, PCA biplot tab -->

## Questions

1. What are the mean income and the mean amount spent on wine for college-educated shoppers?
2. How do spending variables relate to each other, and how does that differ by education level and marital status?

## What it does

| Section | Methods |
| --- | --- |
| Data cleaning | Parses the tab-delimited raw file into a typed data frame; drops non-college education levels and joke marital statuses (`Absurd`, `YOLO`, `Alone`) |
| Question 1 | Histograms and `psych::describe`, then bootstrapped 95% confidence intervals for income and wine spending (`infer`) |
| Question 2 | `GGally` pair plots, PCA biplots, scree plots, and cos² / contribution plots (`FactoMineR`, `factoextra`) |
| RDA | Redundancy analysis (`vegan`): spending as a predictor of demographics and vice versa, then refined models |
| Extras | Violin plots of income by education level, before and after removing outliers |

### Results

- Mean income was about **$53,600** and mean wine spending was about **$324**, with bootstrapped confidence intervals around both.
- The PCA biplots show which spending categories drive the main axes of variation.
- Neither RDA direction (spending → demographics or demographics → spending) explained a large share of the variance. The PCA had already hinted at that weak relationship.

## Running it

Install the R packages once:

```r
install.packages(c(
  "rmarkdown", "tidyverse", "FactoMineR", "factoextra", "ade4", "ExPosition",
  "moderndive", "plotly", "lme4", "GGally", "scatterplot3d", "skimr", "ISLR",
  "infer", "psych", "vegan", "RColorBrewer", "shiny", "ggpubr"
))
```

Then render the report from the repo root:

```r
rmarkdown::render("MATH_271-Final-Project.Rmd")   # → MATH_271-Final-Project.html
```

Or open the `.Rmd` in RStudio and click **Knit**.

## Files

| File | Purpose |
| --- | --- |
| `MATH_271-Final-Project.Rmd` | The full analysis and report |
| `marketing_campaign.csv` | Raw dataset (tab-delimited despite the `.csv` extension) |
| `RAWCSV.PNG`, `CLEANCSV.PNG` | Before/after screenshots of the data frame, embedded in the report |

## Data

[Customer Personality Analysis on Kaggle](https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis). It covers 2,240 customers, with demographics (birth year, education, marital status, income, kids), spending by product category, purchase channels, and campaign responses.
