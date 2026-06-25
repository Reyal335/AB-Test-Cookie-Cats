# Cookie Cats A/B Test Analysis

This project explores an A/B test for the Cookie Cats mobile game, where players were assigned to different versions of the game based on when the first gate appeared.

The main objective is to evaluate whether changing the gate placement affects player engagement and retention.

## Project Overview

The experiment compares two versions:

- Control: players encounter the first gate at level 30
- Treatment: players encounter the first gate at level 40

The analysis focuses on whether these two versions lead to meaningful differences in:

- Day-1 retention
- Day-7 retention
- Total number of game rounds played

## Dataset

The dataset is stored in [data/cookie_cats.csv](data/cookie_cats.csv) and contains the following columns:

- userid: unique player identifier
- version: experiment group (`gate_30` or `gate_40`)
- sum_gamerounds: total number of game rounds played
- retention_1: whether the player returned within 1 day
- retention_7: whether the player returned within 7 days

## Repository Structure

- [notebooks/Z0_CookieCats_AB_Test.ipynb](notebooks/Z0_CookieCats_AB_Test.ipynb): exploratory analysis, retention comparisons, and hypothesis testing
- [notebooks/Z1_SK_test.ipynb](notebooks/Z1_SK_test.ipynb): additional statistical testing and modeling work
- [data/cookie_cats.csv](data/cookie_cats.csv): the experiment dataset

## Analysis Approach

The notebooks walk through the following steps:

1. Load and inspect the dataset
2. Explore retention patterns by group
3. Compare retention rates using proportion-based hypothesis tests
4. Compare average game rounds played using Welch's t-test
5. Investigate logistic regression approaches for modeling retention outcomes

## Tools and Libraries

This project uses Python libraries such as:

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- statsmodels
- scikit-learn

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

4. Open the notebooks in the [notebooks](notebooks) folder and run them in order.

## Notes

This project is a practical example of A/B testing and statistical inference in a product analytics context. It demonstrates how to test for treatment effects, interpret p-values, and reason about business impact from experimental data.
