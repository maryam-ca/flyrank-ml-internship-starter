# Capstone Report — <your lane>

- **Author:**Maryam Fatima
- **Lane:**Refresh / Content Opportunity Scoring
- **Repo:**https://github.com/maryam-ca/flyrank-ml-internship-starter
- **Date:** 5 August 2026

> Copy this file to `work/capstone_report.md` and fill it in as you build. Sections 1–8
> mirror the Pass / Needs-Work rubric axes, so nothing here is optional. Sections 0 and 9
> are **paper sections**: your deployed research paper must carry both, and they're here so
> you never rebuild them from memory at ship time.

## 0. Abstract

This project investigates which content pages should be prioritized for refresh using search intelligence signals. The analysis was performed on the FlyRank Internship Starter Dataset containing 30,000 records and 53 features. After data cleaning, feature engineering, and exploratory analysis, a Refresh Opportunity Score was created and machine learning models were trained to classify pages into High, Medium, and Low refresh priority. The Random Forest model achieved 98.6% accuracy and identified content age, content length, and engagement metrics as the strongest indicators of refresh priority. The resulting ranked recommendations provide a practical decision-support framework for planning content updates.

## 1. Problem Framing

This project supports the decision of identifying which content pages should be refreshed first.

The unit of analysis is an individual content page.

The output is a refresh priority (High, Medium, or Low) together with a numerical refresh score.

Editors can use this ranking to prioritize content updates instead of reviewing every page manually.

Machine learning helps combine multiple search and engagement signals into a consistent decision-support system.

## 2. Data Safety

The project uses the FlyRank Internship Starter Dataset containing anonymized search performance data.

The provider_used column was removed because it contained more than 70% missing values.

Identifier columns such as content_id and client_id were never used as machine learning features.

No client names, URLs, domains, credentials, or confidential search queries were included in the analysis.

The project follows FlyRank's public data safety guidelines.

## 3. Baseline

A Decision Tree classifier was selected as the baseline model.

The baseline achieved approximately 98.2% accuracy.

This model provides a simple and interpretable comparison before training a more robust ensemble model.

## 4. Model / Analysis

The final model uses a Random Forest Classifier.

Features included:

- Search Volume
- Competition
- CPC
- Word Count
- Character Count
- Impressions
- Clicks
- Sessions
- Users
- Engagement Rate
- CTR
- Average Position
- Content Age
- Days Since Last Update
- Trend Percentage
- Health Score

The target variable is Refresh Priority, generated from the Refresh Opportunity Score and grouped into High, Medium, and Low classes.

## 5. Evaluation

The dataset was divided into 80% training data and 20% testing data using stratified sampling.

Baseline Model

Decision Tree Accuracy: 98.2%

Final Model

Random Forest Accuracy: 98.6%

The Random Forest model produced more stable predictions while maintaining strong precision and recall across all refresh priority classes.

## 6. Interpretation

Feature importance analysis showed that Content Age was the strongest predictor of refresh priority.

Additional influential features included Character Count, Days Since Last Update, Word Count, and Engagement Rate.

These findings suggest that older content with lower engagement should generally be reviewed before recently updated content.

## 7. Recommendation

The model recommends ranking pages into High, Medium, and Low refresh priority.

High-priority pages should be refreshed immediately.

Medium-priority pages should be reviewed during scheduled content updates.

Low-priority pages should continue to be monitored without immediate changes.

These recommendations provide decision support and should be combined with editorial review before implementation.

## 8. Reproducibility

The project was developed using Python in Google Colab.

Main libraries include:

- pandas
- numpy
- matplotlib
- scikit-learn
- datasets
- huggingface_hub

Random seed: 42

The notebook can be executed from top to bottom to reproduce all preprocessing, modeling, evaluation, and recommendation steps.

## 9. Acknowledgments & Data Credit

Built on the FlyRank ML Internship Dataset.

Data Source:

https://flyrank.ai

This project was completed as part of the FlyRank Machine Learning Internship Capstone.
---

> **Claims checklist before submitting:** observed / measured / directional / decision-support
> **Metrics vs. base rate:** report your task's base rate (majority-class %) next to any
> precision@K or accuracy — a high score can just be a high base rate. AUC / lift over
> baseline are the honest discrimination numbers.
> language everywhere · no causal claims without an experiment or causal design · no
> "predicted Google's algorithm" · no client-identifying details · numbers in this report
> match a fresh re-run.
