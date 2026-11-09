# Zero-Variance MCMC for a Bayesian GARCH Model

Reducing the variance of MCMC estimators with **control variates**, applied to Bayesian estimation of a Normal-GARCH(1,1) model.

Course project for *Monte Carlo methods* (ENSAE Paris, 2024).
**Authors:** Rémi Calvet, Antoine Gilson, Anna Mosaki, Louis Reisse.

Based on:
- A. Mira, R. Solgi, D. Imparato. *Zero variance Markov chain Monte Carlo for Bayesian estimators.* Statistics and Computing, 2013. [doi:10.1007/s11222-012-9344-6](https://doi.org/10.1007/s11222-012-9344-6)
- R. Leluc et al. *Control variate selection for Monte Carlo integration.* Statistics and Computing, 2021. [doi:10.1007/s11222-021-10011-z](https://doi.org/10.1007/s11222-021-10011-z)

## Idea

To estimate $\mathbb{E}_\pi[f]$ from MCMC samples, the zero-variance (ZV) principle replaces $f$ by $\tilde f = f + H\psi$, where $H$ is a Hamiltonian-type operator built from the score of the target $\pi$ and $\psi$ a polynomial trial function. Since $\mathbb{E}_\pi[H\psi] = 0$, the expectation is unchanged; choosing the polynomial coefficients by regression makes the variance of $\tilde f$ much smaller.

## What the notebook does

All of it is in [`Notebook_Final_Projet_GARCH.ipynb`](Notebook_Final_Projet_GARCH.ipynb).

1. The ZV principle in the general case
2. A random-walk Metropolis–Hastings sampler for the GARCH(1,1) parameters, checked on simulated data (recovery of the true parameters, unbiasedness) and applied to real data
3. First-order polynomial control variates, with coefficients estimated by OLS, and the resulting variance reduction
4. Second-order polynomials: the number of control variates grows quickly, so LASSO is used to select them (compared with full OLS)
5. Bonus: validity of the regression step when MCMC samples are correlated, using subsampling
