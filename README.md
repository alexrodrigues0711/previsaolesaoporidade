# European Football Injury Analysis & Modeling (2020-2025)

## Overview
This project performs an Exploratory Data Analysis (EDA) and builds a Generalized Linear Model (GLM) to statistically analyze the factors influencing the recovery time of football players in major European leagues. 
The primary objective is to determine how injury severity, player position, league, and age impact the duration of absence (`Days_clean`).

## Data Source
The dataset covers injuries from the 2020-2021 to 2024-2025 seasons across the top 5 European leagues. 
**Source:** [European Football Injuries 2020-2025 (Kaggle)](https://www.kaggle.com/datasets/sananmuzaffarov/european-football-injuries-2020-2025/versions/2?resource=download)

## Methodology

### 1. Data Preprocessing
* **Cleaning:** Removed extreme outliers (injuries exceeding 365 days) to prevent model distortion.
* **Feature Engineering:**
    * **Injury Categorization:** Grouped specific injury types into four severity levels: Severe (e.g., ACL tears), Moderate-Severe (e.g., hamstring), Moderate-Light, and Other.
    * **Position Grouping:** Consolidated positions into major tactical roles.
    * **Age Centering:** Centered player age around the median (26 years) for better intercept interpretation.

### 2. Statistical Modeling
Given the target variable (days out) is continuous, strictly positive, and right-skewed, a Generalized Linear Model (GLM) was selected over standard OLS regression.

* **Model Family:** Gamma Distribution
* **Link Function:** Log-link
* **Equation:**
$$\log(E[Y]) = \beta_0 + \beta_1X_1 + \dots + \beta_nX_n$$

## Key Findings
The GLM results highlight significant correlations (p < 0.05) across several dimensions:

* **Injury Severity:** This is the dominant predictor. Compared to "Light" injuries, "Severe" injuries increase the expected recovery time exponentially (Coefficient: 2.18).
* **League Impact:** The Premier League (baseline) is associated with longer recovery times compared to other leagues. Controlling for injury type, players in Serie A and La Liga tend to return to the pitch faster.
* **Positional Differences:** Goalkeepers have the longest average recovery times. Field players, particularly Attacking Midfielders and Wingers, show significantly shorter recovery periods relative to goalkeepers.
* **Age Dynamics:** The model indicates a slight negative coefficient for age. This counter-intuitive finding suggests a "survivorship bias"—older players who remain active in top-tier leagues are likely physically exceptional or manage their fitness differently than younger cohorts.

## Requirements
To replicate this analysis, the following Python libraries are required:
* `pandas`
* `numpy`
* `statsmodels`
* `matplotlib`
* `seaborn`

## Usage
1. Clone this repository.
2. Download the dataset from the link provided in the Data Source section above.
3. Run the analysis script to generate the GLM summary and visualizations.
