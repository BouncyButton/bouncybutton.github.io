---
file_format: mystnb
kernelspec:
  name: python3
---

# Methods in rule learning

Rule learning methods are usually *inductive* in nature, which means that they extract, or learn, rules from data. The
process of learning rules from data is called *rule induction*.

## Rule representation

The preferred way to represent a rule is in the form of an *if-then* statement. For example, a rule could be represented
as:

$$
r : \{0, 1\}^d \rightarrow \{0, 1\}

\begin{cases}
r(x) &= 1 & \text{if } r \text{ covers } x, r \succeq x \\\
& = 0 & \text{otherwise}
\end{cases}
$$

```{code-cell} python
def r(x):
    return x[0] == 1
    
r([1, 0, 0])

```

where $r$ is the rule, $x$ is an instance, and $r$ covers $x$ if the rule is true for the instance.

Other valid representation are:

$$
c \leftarrow f_1 \land f_2 \land \ldots \land f_L
$$

where $c$ is the class value, and $f_i$ are the features.

A Prolog-like representation is also common:

```prolog
ci :- f1, f2, ..., fL.
```