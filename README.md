# Bayesian Analysis of Housing Price Prediction

## Table of Contents
- [Introduction](#introduction)
- [Dataset Overview](#dataset-overview)
- [Data Cleaning and Preprocessing](#data-cleaning-and-preprocessing)
- [Models](#models)
  - [Uninformative Gaussian Prior Model](#uninformative-gaussian-prior-model)
  - [Modified Priors Model](#modified-priors-model)
- [Computation and Diagnostics](#computation-and-diagnostics)
- [Results and Discussion](#results-and-discussion)
- [Conclusion](#conclusion)
- [License](#license)
- [Contributors](#contributors)

## Introduction
This project focuses on using Bayesian analysis to predict housing prices. We explore the relationship between house prices and features such as square footage, number of bedrooms and bathrooms, neighborhood type, and year built. We employ two models, one using uninformative Gaussian priors and another with modified priors, to predict housing prices and understand the significance of different factors.

## Dataset Overview
The dataset used in this analysis consists of various housing attributes:
- **SquareFeet**: The size of the house in square feet.
- **Bedrooms**: The number of bedrooms in the house.
- **Bathrooms**: The number of bathrooms in the house.
- **Neighborhood**: A categorical variable representing the type of neighborhood (Rural, Suburb, Urban).
- **YearBuilt**: The year the house was built.
- **Price**: The target variable representing the house price.

This dataset provides valuable insights into the factors that affect house prices in different areas.

## Data Cleaning and Preprocessing
We performed the following preprocessing steps:
- **Handling missing values**: Missing data was handled using appropriate strategies such as imputation.
- **Feature encoding**: The categorical feature 'Neighborhood' was encoded into numerical values (1 for Rural, 2 for Suburb, and 3 for Urban).
- **Standardizing the features**: Continuous features such as SquareFeet, Bedrooms, and Bathrooms were standardized to bring them to the same scale.

The dataset was split into training and test sets, ensuring that the model would generalize well to unseen data.

## Models

### Uninformative Gaussian Prior Model
The first model used an uninformative Gaussian prior (dnorm(0, 0.001)) for regression coefficients. This model assumes minimal prior knowledge and lets the data guide the analysis. The priors for the intercept (alpha) and precision (tau) were also chosen to be Gaussian and Gamma, respectively.

### Modified Priors Model
In the second model, we updated the priors for regression coefficients to (dnorm(0, 0.01)) to improve model interpretability. The priors for the intercept (alpha) and precision (tau) were also modified to (dnorm(0, 0.01)) and (dgamma(0.5, 0.5)), respectively. This modification was intended to allow for more nuanced exploration of the features' significance.

## Computation and Diagnostics
The analysis was conducted using the JAGS package in R, where the following steps were performed:
- **Model fitting**: The models were fit using MCMC sampling with 2 chains and 10,000 iterations, with a burn-in phase of 5,000 samples.
- **Convergence diagnostics**: Convergence was confirmed using trace plots, Gelman-Rubin statistics (PSRF = 1), and Effective Sample Size (ESS).
- **Model comparison**: The models were evaluated using Deviance Information Criterion (DIC) to assess their relative performance.

## Results and Discussion

### Model Performance
Both models showed similar performance in predicting housing prices. The Deviance Information Criterion (DIC) for the uninformative Gaussian prior model was 982.9, while the modified priors model had a DIC of 983.1. These values suggest that both models are comparable in terms of fit.

### P-Value Analysis
The p-values for model parameters were close to 1 and 0, indicating that some features might not significantly affect the predictions. However, this discrepancy between the model's convergence and the p-values suggests that further refinement is needed to improve the model's fit to the data.

### Model Comparison
The models, despite using different priors, showed similar performance. The uninformative Gaussian prior model is simpler and provides a more straightforward interpretation, while the modified priors model provides a slightly more refined approach.

## Conclusion
The Bayesian analysis provides valuable insights into housing price predictions. While both models showed similar performance, the uninformative Gaussian prior model is preferred for its simplicity and interpretability. Future work could explore incorporating additional features or refining the priors further to improve prediction accuracy.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributors
- **Brandon Agusta Wijaya**
- **Davin Edbert Santoso**
- **Nicholas Sugijono**
- **Steve Marcello Liem**
- **Wilson Gregory Pribadi**
