# Cookie Cats A/B Test Analysis

This project presents an end-to-end A/B test analysis of the Cookie Cats mobile game to evaluate whether moving the first progression gate changes player engagement and retention.

The analysis is designed as a product analytics case study and demonstrates a full statistical workflow: data validation, exploratory analysis, hypothesis testing, model-based inference, and business-focused interpretation of results.

## Business Question

The core question is:

**Does moving the first gate from level 30 to level 40 improve or hurt player retention and engagement?**

This matters because gate placement can influence early player progression, session length, churn, and long-term retention.

## Experiment Design

Players were randomly assigned to one of two game versions:

- **Control:** first gate appears at level 30
- **Treatment:** first gate appears at level 40

The experiment evaluates whether the treatment affects:

- **Day 1 retention** (`retention_1`)
- **Day 7 retention** (`retention_7`)
- **Total game rounds played** (`sum_gamerounds`)

## Dataset

The dataset is stored in [`data/cookie_cats.csv`](data/cookie_cats.csv) and contains the following fields:

- `userid`: unique player identifier
- `version`: experiment group (`gate_30` or `gate_40`)
- `sum_gamerounds`: total number of rounds played
- `retention_1`: whether the player returned within 1 day
- `retention_7`: whether the player returned within 7 days

## Statistical Analysis Overview

The notebooks implement a structured statistical analysis to estimate the treatment effect and determine whether observed differences are likely due to chance.

### 1. Data Loading and Quality Checks

The first step is to load the dataset and inspect:

- data types
- missing values
- balance across experiment groups
- outcome distributions
- duplicate or anomalous records

This validates that the dataset is suitable for inference and that the experiment groups are comparable.

### 2. Exploratory Data Analysis

The analysis includes summary statistics and visualization to understand player behavior across both versions of the game.

Typical EDA steps include:

- comparing retention rates by experiment group
- visualizing the distribution of game rounds played
- checking skewness and outliers in engagement metrics
- examining early-player behavior patterns

This helps identify whether the treatment appears to shift player engagement before formal testing.

### 3. Retention Analysis

Retention is analyzed as a binary outcome for both Day 1 and Day 7.

The project compares:

- proportion of retained users in each group
- absolute differences in retention
- practical significance of observed changes

Because retention is binary, proportion-based statistical methods are used rather than only mean comparisons.

### 4. Hypothesis Testing for Retention

The notebook applies hypothesis testing to determine whether retention differs significantly between the two versions.

Standard framework:

- **Null hypothesis:** retention is the same in both groups
- **Alternative hypothesis:** retention differs between groups

The analysis evaluates whether the observed differences are large enough to reject the null hypothesis at conventional significance levels.

### 5. Welch’s t-Test for Engagement

To compare `sum_gamerounds` between groups, the analysis uses **Welch’s t-test**.

This is appropriate because:

- the groups are independent
- sample sizes may differ
- variance in game rounds is often unequal
- the distribution of gameplay activity is typically skewed

The test assesses whether mean engagement differs meaningfully between control and treatment.

### 6. Distribution and Outlier Considerations

Game-round data in mobile games is usually heavily right-skewed, with a small number of users contributing very large values.

The analysis addresses this by:

- inspecting the shape of the distribution
- identifying extreme values
- interpreting the mean in the context of skewed behavior

This improves interpretation beyond a single summary statistic.

### 7. Logistic Regression for Retention Modeling

The project also explores **logistic regression** as a model-based approach for binary retention outcomes.

This allows estimation of:

- the relationship between experiment version and retention
- the direction and magnitude of the treatment effect
- probabilistic inference for retention behavior

Logistic regression is especially useful because retention is naturally modeled as a probability.

### 8. Statistical Interpretation

Results are interpreted from both a statistical and product perspective:

- **p-values** are used to assess evidence against the null hypothesis
- **confidence intervals** help quantify uncertainty in estimated effects
- **effect size** is considered alongside significance
- business implications are discussed in terms of retention and engagement tradeoffs

This avoids overreliance on statistical significance alone.

## Methods and Tools

The analysis uses standard Python data science and statistical libraries, including:

- `pandas` for data manipulation
- `numpy` for numerical operations
- `matplotlib` and `seaborn` for visualization
- `scipy` for statistical testing
- `statsmodels` for inferential modeling
- `scikit-learn` for modeling utilities

## Repository Structure

- [`notebooks/Z0_CookieCats_AB_Test.ipynb`](notebooks/Z0_CookieCats_AB_Test.ipynb): exploratory analysis, retention comparison, and hypothesis testing
- [`notebooks/Z1_SK_test.ipynb`](notebooks/Z1_SK_test.ipynb): additional statistical testing and modeling work
- [`data/cookie_cats.csv`](data/cookie_cats.csv): the experiment dataset

## Key Skills Demonstrated

This project demonstrates skills relevant to data science, product analytics, and experimentation:

- A/B test design and interpretation
- hypothesis testing for binary and continuous outcomes
- retention analysis
- exploratory data analysis
- statistical modeling with logistic regression
- experimental result communication
- business-oriented decision support

## How to Run

1. Clone the repository
2. Install the required Python packages:

   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn jupyter
   ```

3. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

4. Open the notebooks in the [`notebooks`](notebooks) folder and run them in order.

## Summary

This project is a practical example of A/B testing and statistical inference applied to a real product analytics problem. It shows how to evaluate experimental treatment effects, compare retention and engagement outcomes, and translate statistical findings into product insight.
