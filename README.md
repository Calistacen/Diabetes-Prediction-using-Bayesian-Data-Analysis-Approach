# Diabetes Prediction using Bayesian Data Analysis Approach
A final project applying **Bayesian inference** to model the probability of diabetes occurrence based on health indicators.   This analysis uses a **Bayesian logistic regression model** with **Bernoulli likelihood** and **Gaussian priors**, implemented via **JAGS** and **R**.


## Dataset Information
- **Source:** Pima Indians Diabetes Dataset  
- **Observations:** 768  
- **Variables:** 9  
- **Target Variable:** `Outcome` (0 = no diabetes, 1 = diabetes)  
- **Predictors:**
  - Pregnancies  
  - Glucose  
  - BloodPressure  
  - SkinThickness  
  - Insulin  
  - BMI  
  - DiabetesPedigreeFunction  
  - Age  

##  Model Overview

The model assumes a **Bernoulli likelihood** with the logic:

- each person’s outcome (whether diabetic or not) is assumed to follow a Bernoulli distribution, meaning it represents a binary event (0 = no diabetes, 1 = diabetes).
- The model predicts the probability of having diabetes using a logistic (logit) link function, which connects the probability to the input variables (like glucose, blood pressure, BMI, etc.).
- Each coefficient in the model (for every input variable) has a Gaussian prior centered at 0 with small variance. This reflects the assumption that most features have a modest effect unless the data strongly suggest otherwise.

##  Why Bayesian Approach?

- It provides uncertainty estimates for every parameter (posterior distributions).
- It allows probabilistic interpretation instead of just point estimates.
- The model can incorporate prior knowledge about medical factors if available.
- The posterior summaries (mean, credible intervals) show not just which features matter, but how confidently we can say that.

  
## Implementation Details

- **Language:** R  
- **Bayesian Inference Engine:** JAGS (`rjags` package)  
- **Steps:**
  1. Train-test split (80/20)
  2. Model definition and prior setup
  3. MCMC sampling with 3 chains × 5000 iterations
  4. Posterior summary and convergence diagnostics

## Results

- MCMC convergence achieved (stable trace plots and Gelman–Rubin < 1.1)  
- Positive association detected between **Glucose**, **BMI**, and **Outcome** probability  
- Posterior summaries provide credible intervals for each coefficient  
- Posterior predictive checks indicate reasonable fit


## Key Insights
- Glucose is the **strongest predictor** of diabetes in the dataset.  
- Age and BMI also contribute significantly to posterior probability.  
- Bayesian modeling captures **uncertainty** around coefficients and outcomes better than classical logistic regression.

for further information can be checked in the essay file


##  Tools & Libraries
- R  
- `rjags` — MCMC simulation  
- `coda` — posterior diagnostics  
- `ggplot2` — visualization  

---

##### This project are made for educational purposes only by Calista.L

