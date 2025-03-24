---
file_format: mystnb
kernelspec:
  name: python3
---

# Structure of rule-based models

A rule by itself can be useful, but it is usually not enough to solve a problem. Rules are usually aggregated into more
complex structures, that can be either flat/hierarchical (most studied) or deep (more recently studied).

- **Flat**: a set of rules can be combined in a DNF (Disjunctive Normal Form). Can perform **concept learning**, where there are no negative examples.
    1. **Rule sets**: a set of rules that are combined using ORs. 
- **Hierarchical**: an **ordered** sequence of rules with a default rule. Used for classification.
    1. **Rule lists**: each rule yields a possibly different prediction.
    2. **Weighted**: each rule is assigned a weight, which is used to combine the rules.
- **Deep**: rules are used into a multi-step process.
    1. **Binary trees**: a tree-like structure where each node is a rule.
    2. **Multilayer**: a set of rules that are combined in a multilayer structure.


First, let's consider the following propositions:

```{code-cell} python
from itertools import product
def A(x):
    return x[0] == 1

def B(x):
    return x[1] == 1

def C(x):
    return x[2] == 1
    
X = list(product([0, 1], repeat=4))

def show_truth_table(f, X):
    import pandas as pd
    results = [f(x) for x in X]
    df = pd.DataFrame(X, columns=['A', 'B', 'C', 'D'])
    df.set_index(['A', 'B', 'C', 'D'], inplace=True)
    df['result'] = results
    return df
```


Here follows some examples.

# Rule sets 
A rule set can be expressed as a DNF (Disjunctive Normal Form) formula. Each rule is combined using an OR operator.

```{code-cell} python
def rule_set(x):
    if A(x) and B(x):
        return 1
    if B(x) and C(x):
        return 1
    return 0

show_truth_table(rule_set, X)
```

# Rule lists
A rule list contains different consequents for each rule. The **first** rule that fires is the one that is used. 

It also has a default rule, which is used when no rule is satisfied.

```{code-cell} python
def rule_list(x):
    if A(x) and B(x):
        return 0
    if B(x) and C(x):
        return 1
    # default rule
    return 0

show_truth_table(rule_list, X)
```

# Weighted

Each rule can be assigned a weight, which is used to combine the rules (e.g., with a weighted sum). Arguably this loses in interpretability but can be more accurate.

```{code-cell} python
def weighted(x):
    w1, w2 = 0.5, -0.6
    total = 0
    if A(x) and B(x):
        total += w1
    if B(x) and C(x):
        total += w2
    return int(total > 0.0)

show_truth_table(weighted, X)
```

# Decision tree

```{code-cell} python
def binary_tree(x):
    if A(x):
        if B(x):
            return 1
        else:
            return 0
    else:
        if C(x):
            return 1
        else:
            return 0

show_truth_table(binary_tree, X)
```

# Multilayer

A multilayer representation can be more compact, and is theoretically always possible to convert a multilayer representation into a flat one (i.e., it's **not** more expressive!)


```{code-cell} python
def multilayer(x):
    h1, h2 = 0, 0
    if (A(x) and B(x)) or (B(x) and C(x)):
        h1 = 1
    if B(x) or C(x):
        h2 = 1
        
    if h1 and h2:
        return 1
    if h2:
        return 0
    return 0

show_truth_table(multilayer, X)
```


![Flat vs deep](../images/flat-vs-multilayer.png)