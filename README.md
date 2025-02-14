# Binary Choice Model Estimation
This repository contains GAUSS code for simulating and estimating binary response models under two scenarios: No Heteroskedasticity (no-Het Model) and Heteroskedasticity (Het Model). The code uses maximum likelihood estimation (via the GAUSS maxlik library) to estimate model parameters and computes marginal effects and a Wald test for heteroskedasticity.

## Overview
The simulation performs the following steps.
### Data Generation
For each replication (25 replications in total), the code generates data for 3000 observations. Two seeds (and variations) are used to simulate the independent variables (X) and error terms (w). The latent variable is computed as a linear function of X (with coefficients [1, 1, 0]), and binary outcomes are obtained by comparing this to a random draw. For the heteroskedastic model, the error term is scaled by a factor S (which is an exponential function of the first two predictors).

### Estimation
For the No-Het model, The parameters are first initialized using OLS estimates and then refined by maximizing the log-likelihood (computed in the prob procedure).

Similar to the No-Het case but with an additional set of parameters accounting for the heteroskedasticity, using the Hprob likelihood function for the Het-model.

### Marginal Effects Calculation
For both models, the code calculates the marginal effects. It also evaluates the effects at different quantiles (first and third quartiles) of one of the predictors.

### Wald Test
A Wald test is conducted for the heteroskedastic parameters to assess the joint significance of the heteroskedasticity effects.

### Output
The results (mean estimates, standard deviations, marginal effects, and test statistics) are printed to the console.

## How To Run
### Requirements
GAUSS software with maxlik library.
