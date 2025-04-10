# What is rule learning?

Under the broad rule learning umbrella we find many different works, from the early days of expert systems to the most recent [resurgence](https://arxiv.org/pdf/2012.05876) in interpretable and neuro-symbolic AI.

## Rules

Broadly speaking, a rule defines **relationships**. For example, consider the following problem.

### Problem

Imagine you are in an ice cream shop. You are trying to understand the behavior of the customers to choose the best strategy to increase sales.

### Data

You have a dataset with the following columns: 

- **Inputs**
  1. Cone (boolean)
  2. Ice cream (boolean)
  3. Three flavors chosen (boolean)
  4. Give discount (boolean)
  5. Chocolate available (boolean)
- **Output**
  1. High spender (boolean)
  2. Happy customer (boolean)
  3. Returning customer (boolean)

Possible rules are:

1. If I buy a cone, then I will buy ice cream too ([association rule](../symbolic/inference.md))
2. If I choose three flavors, then I'm likely to be a high spender ([classification rule](../symbolic/inference.md))
3. If I am a returning customer, it means I am a happy customer ([learning constraints](../symbolic/inference.md))

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
\text{Give discount} \rightarrow \text{Happy customer}
$$

### Rule sets

A rule set can be expressed as a DNF (Disjunctive Normal Form) formula. Each rule is combined using an OR operator.

$$
\text{Chocolate available} \land \text{Three flavors} \\
\vee \\
\text{Give discount} \\
\rightarrow \text{Returning customer}
$$

### Rule lists

RIPPER is a well-known algorithm to learn rule lists from data.

$$
\text{Three flavors} \land \text{Give discount} \rightarrow \text{Returning customer}, \\
\neg \text{Chocolate available}  \land \neg \text{Give discount}  \rightarrow \neg \text{Returning customer}
$$

### ILP (Inductive Logic Programming)

ILP is a field that combines logic programming with machine learning. It can be used to learn rules from data.

$$
\text{Buys}(X, Y) \land \text{Likes}(X) \land \text{PairsWell}(X, Y) \rightarrow \text{Likes}(Y)
$$

# Rule representation

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
c \leftarrow f_1 \land f_2 \land \ldots \land f_L \\
f_1 \land f_2 \land \ldots \land f_L  \rightarrow c \\
(a_1 = v_1) \land (a_2 = v_2) \land \ldots \land (a_L = v_L) \rightarrow c 
$$

where $c$ is the class value, and $f_i$ are the features.

A Prolog-like representation is also common:

```prolog
ci :- f1, f2, ..., fL.
```