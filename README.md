# Cohort Retention and Churn Analysis in R Using Survival Analysis

## Overview

This project investigates customer retention and churn patterns using **survival analysis in R**. It examines how long customers remain active, compares retention performance across acquisition channels, and identifies factors associated with customer attrition.

Rather than treating churn as a simple binary outcome, the analysis models the time until a customer becomes inactive while accounting for customers who have not yet churned (right-censored observations).

The project combines survival analysis with cohort analysis and funnel visualisation to provide a comprehensive view of customer behaviour.

## Objectives

- Measure customer retention and time to churn.
- Estimate customer survival probabilities using Kaplan–Meier methods.
- Compare retention patterns across acquisition channels.
- Test whether differences between acquisition channels are statistically significant.
- Identify factors associated with customer churn using a Cox proportional hazards model.
- Examine retention trends across customer acquisition cohorts.
- Analyse customer progression and drop-off through a conversion funnel.

## 1. Kaplan–Meier Survival Analysis

The Kaplan–Meier estimator measures the probability that a customer remains active beyond a given period.

\[
\hat{S}(t)=\prod_{t_i\leq t}
\left(1-\frac{d_i}{n_i}\right)
\]

Where:

- \(t_i\) represents an observed churn time.
- \(d_i\) represents the number of churn events at time \(t_i\).
- \(n_i\) represents the number of customers at risk immediately before \(t_i\).

The analysis produces Kaplan–Meier survival curves to visualise customer retention over time.

Customers are grouped by acquisition channel to examine differences in retention patterns.

## 2. Log-Rank Test

The log-rank test compares survival distributions across acquisition channels.

It evaluates the null hypothesis:

\[
H_0:S_1(t)=S_2(t)=\cdots=S_k(t)
\]

The test determines whether observed differences in customer retention curves are statistically significant.

The results help establish whether acquisition channels are associated with meaningfully different customer retention patterns.

## 3. Cox Proportional Hazards Model

The Cox proportional hazards model examines the relationship between customer characteristics and the instantaneous risk of churn.

\[
h(t|X)=h_0(t)\exp(\beta_1X_1+\cdots+\beta_pX_p)
\]

The analysis uses hazard ratios to interpret the direction and magnitude of associations.

- Hazard ratio greater than 1: Higher instantaneous churn risk.
- Hazard ratio below 1: Lower instantaneous churn risk.
- Hazard ratio equal to 1: No difference in instantaneous churn risk.

Acquisition channel is included as a key explanatory variable, alongside other available customer characteristics.

The proportional hazards assumption is assessed using Schoenfeld residuals and appropriate diagnostic plots.

## 4. Cohort Retention Analysis

A cohort analysis groups customers according to their acquisition period and tracks their subsequent activity.

The cohort retention heatmap presents retention rates across successive periods.

It helps identify:

- Differences in retention between acquisition cohorts.
- Periods when customer attrition is highest.
- Cohorts with stronger or weaker long-term retention.
- Potential changes in retention patterns over time.

## 5. Customer Funnel Analysis

The funnel breakdown examines customer progression through defined stages of the customer journey.

Depending on the available data, stages may include:

1. Acquired customers.
2. Registered or onboarded customers.
3. First purchase.
4. Repeat purchase.
5. Retained or active customers.

The analysis calculates conversion and drop-off rates between stages, highlighting where customers are most likely to disengage.

## 6. R Implementation

The analysis is implemented in R using relevant statistical and visualisation packages.

| Package | Purpose |
|---|---|
| `survival` | Kaplan–Meier estimation, log-rank testing and Cox regression |
| `survminer` | Survival curves and model diagnostics |
| `dplyr` | Data cleaning and transformation |
| `ggplot2` | Statistical visualisations |
| `tidyr` | Cohort data restructuring |
| `readr` | Data import and export |

## 7. Expected Outputs

The project produces:

- Kaplan–Meier survival curves by acquisition channel.
- Log-rank test results.
- Cox proportional hazards model estimates and hazard ratios.
- Proportional hazards diagnostic plots.
- Cohort retention heatmap.
- Customer conversion funnel.
- Summary tables highlighting retention and churn patterns.

## 8. Interpretation and Business Applications

The findings can help businesses:

- Identify acquisition channels associated with stronger customer retention.
- Understand when customers are most likely to churn.
- Identify customer characteristics associated with higher churn risk.
- Compare retention performance across acquisition cohorts.
- Locate customer journey stages with the greatest drop-off.
- Inform customer engagement and retention strategies.

## Conclusion

This project demonstrates the application of survival analysis to customer retention and churn. By combining Kaplan–Meier estimation, log-rank testing and Cox proportional hazards modelling with cohort and funnel analysis, it provides both statistical and practical insights into customer behaviour.

The emphasis is on understanding not only how many customers leave, but also **when they leave, how retention differs across acquisition channels, and which factors are associated with churn**.

*Note: Survival analysis requires customer-level observation periods, event indicators and appropriate censoring information. Findings depend on data quality, the definition of churn and the validity of model assumptions.*
