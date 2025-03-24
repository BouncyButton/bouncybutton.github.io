# What is rule learning?

Under the broad rule learning umbrella we find many different works, from the early days of expert systems to the most recent [resurgence](https://arxiv.org/pdf/2012.05876) in interpretable and neuro-symbolic AI.

## Rules

Broadly speaking, a rule defines **relationships**. For example, consider the following problem.

### Problem

Imagine you are in an ice cream shop. You are trying to understand the behavior of the customers to choose the best strategy to increase sales.

### Data

You have a dataset with the following columns: 

- ...

Possible rules are:

1. If I buy a cone, then I will buy ice cream too ([association rule](../symbolic/inference.md))
2. If I choose three flavors, then I'm likely to spend more than 10 dollars ([classification rule](../symbolic/inference.md))
3. If I spend more than 100 dollars, then I'm likely to be a high spender ([learning constraints](../symbolic/inference.md))

For rule representation, see [rules](../intro/inference.md).

## Examples

### Association rules

APriori is a well-known algorithms to mine association rules from transactions. 

$$
\text{Cone} \rightarrow \text{Ice cream}
$$

### Classification rules

LearnOneR can be used to learn classification rules from data. This is also called **rule induction**.

$$
\text{Ice cream} \rightarrow \text{High spender}
$$

### Rule lists

RIPPER is a well-known algorithm to learn rule lists from data.

$$
\text{Three flavors} \rightarrow \text{More than 10 dollars}
\text{...} \rightarrow \text{...}
$$

### ILP (Inductive Logic Programming)

ILP is a field that combines logic programming with machine learning. It can be used to learn rules from data.

$$
\text{...} \rightarrow \text{...}
$$

