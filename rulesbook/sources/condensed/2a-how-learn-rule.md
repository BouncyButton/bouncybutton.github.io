# How to infer new rules

To infer a rule, it is needed to define two things:

1. Its antecedent, which is the condition that must be satisfied for the rule to be true.
2. Its consequent, which describes what the rule entails.

A consequent can be inferred from a set of examples by estimating the most frequent class in the selected data (**maximum likelihood** with possibly **laplace smoothing**).

An antecedent can be inferred from data in many ways.
- with an association rule learning algorithm (e.g., [Apriori](../symbolic/apriori.md), [FPGrowth](../symbolic/fpgrowth)).
  This choice is done by [Bayesian Rule Sets](../symbolic/brs) and [Bayesian Rule Lists](../symbolic/brl).
- through a seed example (e.g., [AQ](../symbolic/aq.md), [Find-RS](../symbolic/find-rs.md)).

Some procedures learn the antecedent and the consequent jointly:
- [LearnOneR](../symbolic/learn-oner.md) uses hill climbing to find a rule, in a general-to-specific search.
- [RIPPER](../symbolic/ripper.md)'s GrowRule procedure uses a sequential covering strategy to find new rules.