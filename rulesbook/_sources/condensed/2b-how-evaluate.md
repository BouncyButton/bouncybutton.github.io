---
file_format: mystnb
kernelspec:
  name: python3
---

# How to evaluate a rule

Not all rules are equal.

The most relevant trade-off for a rule is how much a rule is **specific** vs. how much is **correct**. 
* A rule that is too specific will not be useful to classify many examples (too **incomplete**);
* A rule that is too general will be incorrect for many examples (too **inconsistent**).

![Completeness vs. consistency](consistency.png)

The evaluation of the quality of a rule has been studied since the inception of
AQ ([Michalski, 1969](https://www.semanticscholar.org/paper/On-the-Quasi-Minimal-Solution-of-the-General-Michalski/e3b0fe4c409930f37c0a4be9222e0b21d6471ac7)),
and many metrics have
been proposed.

In particular, we can distinguish, for each class of interest, a partition of our data.

$$
D = P \cup N
$$

we will call $P$ is the set of positive examples and $N$ is the set of negative examples. In the multiclass case, we can
use the same notation, but we will have $P_i$ and $N_i$ for each class $i$.

We also distinguish whether a metric consider only the antecedent of the rule, or the antecedent and the consequent.

```{code-cell} python
def r(x):
    return x[0] == 1

import numpy as np
np.random.seed(0)
from itertools import product

X = list(product([0, 1], repeat=4))
y = np.random.randint(0, 2, len(X))
D = list(zip(X, y))

import pandas as pd
df = pd.DataFrame(X, columns=['A', 'B', 'C', 'D'])
df['y'] = y
df.set_index(['A', 'B', 'C', 'D'], inplace=True)
df
```

### Coverage

The coverage of a rule is the number of **examples** covered by the rule. It is defined as:

$$
\text{coverage}(r) = \frac{\sum_{x \in D} r(x)}{|D|}
$$

```{code-cell} python
def coverage(rule, D):
    return sum([r(x) for x, _ in D]) / len(D)
    
coverage(r, D)
```

Note we **don't** check the class of the example.

### Support

The support of a rule is the number of **positive examples** covered by the rule, over the total number of examples.

In practice, it is a frequency count.

It is defined as:

$$
\text{support}(r) = \frac{\sum_{x \in P} r(x)}{|D|}
$$

```{code-cell} python
def support(rule, data, target=1):
    return sum([r(x) for x, y in data if y == target]) / len(data)
    
support(r, D)
```

### Confidence

The confidence of a rule is the number of **positive examples** covered by the rule, over the total number of examples
covered by the rule.

It is defined as:

$$
\text{confidence}(r) = \frac{\sum_{x \in P} r(x)}{\sum_{x \in D} r(x)}
$$

```{code-cell} python
def confidence(rule, data, target=1):
    return sum([r(x) for x, y in data if y == target]) / sum([r(x) for x, _ in data])
    
confidence(r, D)
```

It can also be considered as the maximum-likelihood estimate for $P(y=1|r)$, the probability of the class given the
rule.

