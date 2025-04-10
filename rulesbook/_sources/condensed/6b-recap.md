# Recap on rule-based models learned with combinatorial optimization techniques

In this chapter, we have covered the following models:

1. Rule-set based models: expressed with DNF (Disjunctive Normal Form) rules.

   a. Find-RS finds a set of rules that cover the positive examples and none of the negative examples.

   b. BRS (Bayesian Rule Sets) uses a Bayesian approach to learn a set of rules.
2. Rule-list based models: expressed with a list of rules.

   a. RIPPER (Repeated Incremental Pruning to Produce Error Reduction) uses a greedy optimization approach to learn a rule list.

   b. Bayesian Rule Lists uses a Bayesian approach to learn a rule list.
3. Deep rule-based models: expressed with a multi-step process.

   a. CART (Classification and Regression Trees) uses a decision tree to learn a set of rules. Each decision inspects only one feature at a time.

   b. DRNC (Deep Rule Network Classifier) is a greedy algorithm that learns a set of rules with intermediate representations. Multiple features are considered at each step, alternating ANDs and ORs.

Pros: 
- Generally interpretable, thanks to explicit simplification/pruning procedures.
- Fast to train with good generalization in small datasets.

Weaknesses:
- **Scales poorly** (usually $O(N^2) - O(N^3)$ complexity, except for CART).
- Still **prone to overfitting** for hard problems.