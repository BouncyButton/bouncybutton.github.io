## How to infer a new rule

To infer a rule it is needed to define two things:

1. its antecedent, which is the condition that must be satisfied for the rule to be true.
2. its consequent, which is the prediction that the rule makes.

An antecedent can be inferred from data in many ways.

- with an association rule learning algorithm (e.g., [Apriori](../symbolic/apriori.ipynb.old), [FPGrowth](../symbolic/fpgrowth)).
  This choice is done by [Bayesian Rule Sets](../symbolic/brs) and [Bayesian Rule Lists](../symbolic/brl).
- jointly with its consequent

The consequent is the result of some type of estimation.

- simple: the consequent is the most frequent class in the data that satisfies the antecedent.
- ...



### 