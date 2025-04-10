---
file_format: mystnb
kernelspec:
  name: python3
---

# Apriori algorithm

The Apriori algorithm has been developed to mine **frequent itemsets** in a dataset. This is relevant for rule learning applications: the space of all possible conjunctive rules is too large to be explored exhaustively, so we need to find a way to reduce the search space. Extracting frequent itemsets makes the process more efficient. It is mainly used to mine association rules, which are rules that describe the relationships between items in a dataset.

## Definitions

* **Itemset**: a subset of one or more items, defined as $X = \{x_1, x_2, \ldots, x_n\} \subseteq I$. For example, in a supermarket dataset, an itemset could be $\{milk, bread\}$.
* **Support**: the frequency of an itemset in the dataset, defined as $support(X) = \frac{\text{count}(X)}{\text{total transactions}}$.
* **Frequent itemset**: an itemset whose support is greater than a predefined threshold $\theta$.

```{code-cell} python
from itertools import combinations

# Helper function to count the frequency of itemsets in the transactions
def count_itemsets(transactions, itemsets):
    itemset_counts = {itemset: 0 for itemset in itemsets}
    for transaction in transactions:
        for itemset in itemsets:
            if set(itemset).issubset(set(transaction)):
                itemset_counts[itemset] += 1
    return itemset_counts
```

## Candidate generation

The Apriori algorithm generates candidate itemsets of size $k$ from the frequent itemsets of size $k-1$. This is done by joining two frequent itemsets if their first $k-1$ items are the same.

The candidate generation is essentially a breadth-first search which is pruned leveraging the **downward closure property** (or **Apriori property**): if an itemset is frequent, then all of its subsets must also be frequent.

Formally:

$$
If supp(X) \ge \theta, \text{ then } \forall Y \subseteq X, supp(Y) \ge \theta
$$

And conversely:

$$
If supp(Y) < \theta, \text{ then } \forall X \supseteq Y, supp(X) < \theta
$$

```{code-cell} python
# Helper function to generate candidate itemsets from previous frequent itemsets
def generate_candidates(prev_frequent_itemsets, k):
    candidates = set()
    prev_frequent_itemsets = list(prev_frequent_itemsets)  # convert to list for indexing
    for i in range(len(prev_frequent_itemsets)):
        for j in range(i + 1, len(prev_frequent_itemsets)):
            # Join two itemsets if their first k-1 items are the same
            itemset1, itemset2 = prev_frequent_itemsets[i], prev_frequent_itemsets[j]
            candidate = tuple(sorted(set(itemset1).union(set(itemset2))))
            if len(candidate) == k:  # Only keep itemsets of length k
                candidates.add(candidate)
    return candidates
```

## Rule generation

An association rule is defined as $X \rightarrow Y$, where $X$ and $Y$ are itemsets and $X \cap Y = \emptyset$. The confidence of a rule is defined as:

$$
\text{confidence}(X \rightarrow Y) = \frac{\text{support}(X \cup Y)}{\text{support}(X)}
$$

Essentially, if the confidence of a rule is high, it means that the presence of $X$ in a transaction implies the presence of $Y$ with high probability. This confidence estimation is a maximum-likelihood estimate.

```{code-cell} python

# Helper function to generate rules from frequent itemsets
def generate_rules(frequent_itemsets, itemset_counts, min_confidence, total_transactions):
    rules = []
    for itemset in frequent_itemsets:
        if len(itemset) > 1:
            # Generate all non-empty subsets of itemset
            for size in range(1, len(itemset)):
                for antecedent in combinations(itemset, size):
                    antecedent = tuple(sorted(antecedent))  # sort to keep consistency
                    consequent = tuple(sorted(set(itemset) - set(antecedent)))

                    # Calculate confidence of the rule: support(X ∪ Y) / support(X)
                    antecedent_support = itemset_counts.get(antecedent, 0) / total_transactions
                    rule_support = itemset_counts.get(itemset, 0) / total_transactions

                    if antecedent_support > 0:
                        confidence = rule_support / antecedent_support
                        if confidence >= min_confidence:
                            rules.append((antecedent, consequent, confidence))
    return rules
```

## Main Apriori function

Finally, we can put all the pieces together to create the main Apriori function. This function takes a list of transactions, a minimum support threshold, and a minimum confidence threshold, and returns the frequent itemsets and association rules.

```{code-cell} python
# Main Apriori function
def apriori(transactions, min_support, min_confidence):
    # Convert transactions to list of sets for easier subset checking
    transactions = [set(transaction) for transaction in transactions]

    # Step 1: Generate candidate 1-item itemsets
    all_items = set(item for transaction in transactions for item in transaction)
    candidate_1_itemsets = [(item,) for item in all_items]

    # Step 2: Count 1-item itemsets and prune by minimum support
    itemset_counts = count_itemsets(transactions, candidate_1_itemsets)
    frequent_itemsets = [itemset for itemset, count in itemset_counts.items() if
                         count / len(transactions) >= min_support]

    # Step 3: Generate higher-order itemsets
    k = 2
    all_frequent_itemsets = frequent_itemsets.copy()  # Store all frequent itemsets
    all_itemset_counts = {**itemset_counts}
    while frequent_itemsets:
        candidate_k_itemsets = generate_candidates(frequent_itemsets, k)
        itemset_counts = count_itemsets(transactions, candidate_k_itemsets)
        frequent_itemsets = [itemset for itemset, count in itemset_counts.items() if
                             count / len(transactions) >= min_support]

        # Add the frequent itemsets of this size to the result
        all_frequent_itemsets.extend(frequent_itemsets)
        all_itemset_counts = {**all_itemset_counts, **itemset_counts}
        k += 1

    # Step 4: Generate association rules
    rules = generate_rules(all_frequent_itemsets, all_itemset_counts, min_confidence, len(transactions))

    return all_frequent_itemsets, rules


min_support = 0.6  # 60%
min_confidence = 0.8  # 70%

transactions = [('eggs', 'bacon', 'soup'),
                ('eggs', 'bacon', 'apple'),
                ('soup', 'bacon', 'banana')]
frequent_itemsets, rules = apriori(transactions, min_support, min_confidence)


print('Frequent itemsets:', frequent_itemsets)
print('Rules:', rules)
```

Let's compare this to an existing implementation.

```{code-cell} python

from apyori import apriori as ap1

# Apply Apriori algorithm
results = ap1(transactions, min_support=0.5, min_confidence=1)

# Print results
for result in results:
    print(result)


from efficient_apriori import apriori as ap2
transactions = [('eggs', 'bacon', 'soup'),
                ('eggs', 'bacon', 'apple'),
                ('soup', 'bacon', 'banana')]
itemsets, rules = ap2(transactions, min_support=0.5, min_confidence=1)
print(rules)  # [{eggs} -> {bacon}, {soup} -> {bacon}]
```

It works!

# References
* https://ocw.mit.edu/courses/15-097-prediction-machine-learning-and-statistics-spring-2012/eb02afbd0a9c32637dd64cdb6b76c2f1_MIT15_097S12_lec01.pdf