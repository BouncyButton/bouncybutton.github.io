# Bayesian rule lists

Bayesian rule lists are a probabilistic-based model. The method employs a prior over rule lists to encourage **sparsity** and leverages Bayesian inference to find the most probable rule set given the data.

## TL;DR
* **Pros:**
  * Estimates probabilities in a sound Bayesian framework.
* **Cons:**
  * Requires costly MCMC sampling.
  * Bounded by the premined association rules.

## Algorithm

* Pre-mine association rules.
* Sample the list length parameter $m$ from a truncated Poisson distribution.
* For the default rule: Sample the Dirichlet-Multinomial distribution parameter  of the target value (i.e., the rule that applies when nothing else applies).
* For decision list rule $j=1,...,m$, do:
  * Sample the rule length parameter $l$ (number of conditions) for rule $j$.
  * Sample a condition of length $l_j$ from the pre-mined conditions.
  * Sample the Dirichlet-Multinomial distribution parameter for the THEN-part (i.e., for the distribution of the target outcome given the rule).
* For each observation in the dataset:
  * Find the rule from the decision list that applies first (top to bottom).  
  * Draw the predicted outcome from the probability distribution (Binomial) suggested by the rule that applies.


## Example

``` Rules from SBRL model
If {body_mass_g=[5.1e+03,6.3e+03]} then p = 0.083
else if {species=Gentoo} then p = 0.873
else if {body_mass_g=[3.9e+03,5.1e+03)} then p = 0.066
else if {bill_depth_mm=[15.9,18.7)} then p = 0.876
else (default rule) then p = 0.333
```

