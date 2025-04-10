---
file_format: mystnb
kernelspec:
  name: python3
---

# Sequential covering algorithms

Sequential covering algorithms are a family of algorithms that iteratively build a set of rules to classify instances. 

* The rules are built one by one.
* Each rule is built to classify instances that are not classified by the previous rules.
* The algorithm stops when all instances are classified (or when a stopping criterion is met).

The original sequential covering algorithm is the **AQ** algorithm, which has been updated many times since its inception. The most popular sequential covering algorithm nowadays is the **RIPPER** algorithm. Other algorithms in this family include Find-RS.

## General algorithm

The general algorithm for sequential covering is as follows:

1. Initialize the set of rules $R = \emptyset$.
2. While there are instances not covered by the rules:
    1. Find the best rule $r$ that covers the most instances.
    2. Add $r$ to $R$.
    3. Remove the instances covered by $r$.

## AQ algorithm

The AQ algorithm is the original sequential covering algorithm. It was introduced by Michalski in 1969.

```{code-cell} python

import numpy as np

class AQAlgorithm:
    def __init__(self, dataset, target_class):
        """
        dataset: List of (feature_vector, label) pairs.
        target_class: The positive class to learn rules for.
        """
        self.dataset = dataset
        self.target_class = target_class
        self.rules = []
    
    def covers(self, rule, example):
        """Checks if a rule covers a given example."""
        return all(f is None or f == e for f, e in zip(rule, example))
    
    def learn(self):
        """Learns a set of classification rules using the AQ algorithm."""
        positives = [x for x, y in self.dataset if y == self.target_class]
        negatives = [x for x, y in self.dataset if y != self.target_class]
        
        while positives:
            seed = positives.pop(0)  # Take first uncovered positive example
            best_rule = self.find_best_rule(seed, negatives)
            self.rules.append(best_rule)
            positives = [p for p in positives if not self.covers(best_rule, p)]
    
    def find_best_rule(self, seed, negatives):
        """Finds the best rule covering the seed example while excluding negatives."""
        rule = list(seed)  # Start with the most specific rule (the seed itself)
        
        for i in range(len(rule)):
            generalizations = rule[:]
            generalizations[i] = None  # Generalize feature i
            
            if not any(self.covers(generalizations, n) for n in negatives):
                rule = generalizations  # Accept generalization if it does not cover negatives
        
        return rule
    
    def predict(self, example):
        """Predicts the class of a given example based on learned rules."""
        for rule in self.rules:
            if self.covers(rule, example):
                return self.target_class
        return "Unknown"  # Default class if no rule applies

# Example usage
dataset = [
    ((1, 'S', 'Red'), 'Positive'),
    ((1, 'M', 'Blue'), 'Negative'),
    ((2, 'L', 'Red'), 'Positive'),
    ((2, 'S', 'Blue'), 'Negative'),
    ((1, 'L', 'Red'), 'Positive')
]

aq = AQAlgorithm(dataset, target_class='Positive')
aq.learn()
print("Learned rules:", aq.rules)
print("Prediction for (1, 'S', 'Red'):", aq.predict((1, 'S', 'Red')))
```

## RIPPER algorithm

RIPPER (Repeated Incremental Pruning to Produce Error Reduction) is a popular sequential covering algorithm that builds a set of rules to classify instances. It was introduced by Cohen in 1995.

The RIPPER algorithm essentially integrates overfitting avoidance by pruning rules that do not improve the classification performance.

```{code-cell} python
...
```

## Find-RS algorithm

Find-RS is another sequential covering algorithm developed by Bergamin and Aiolli in 2023.

![Find-RS algorithm](find-rs.pdf)

### Input:
- $\mathcal{P}$: Set of positive examples  
- $\mathcal{N}$: Set of negative examples  
- $ p_{gen} $: Generalization probability  

### Output:
- Disjunctive Normal Form (DNF) rule  

---

1. **Initialize**  
   $ B, D, k \gets [\; ], [\; ], 0 $

2. **While** $ \mathcal{P} $ is not empty:  
   - $ \mathbf{s} \gets $ pop($ \mathcal{P} $)  *// Pick a starting example*  
   - $ B, D \gets B + \{\mathbf{s}\}, D + \mathbf{s} $  
   - $ B_k \gets B_k \cup \{\mathbf{s}\} $  
   - $ Q \gets [ \; ] $  *// Examples not covered by the rule*  

3. **For each** $ \mathbf{p} \in \mathcal{P} $:  
   - $ \mathbf{r}' \gets $ generalize($ D_k, \mathbf{p} $)  
   - **If** $ \nexists \mathbf{n} \in \mathcal{N} \mid \mathbf{r}' \succeq \mathbf{n} $:  
     - $ B_k \gets B_k \cup \{\mathbf{p}\} $  
     - $ D_k \gets \mathbf{r}' $  *// Update the last rule*  
   - **Else**:  
     - $ Q \gets Q + \mathbf{p} $  
    
4. **Update Positive Set**:  
   - $ \mathcal{P} \gets Q $  
   - $ k \gets k + 1 $  

5. **Simplify and Generalize**:  
   - $ B, D \gets $ simplify($ B, D $)  *// See Algorithm~\ref{alg:pruning}*  
   - $ B, D \gets $ generalize($ \mathcal{N}, D, p_{gen} $)  *// See Algorithm~\ref{alg:generalization}*  

6. **Return** $ B, D $


## Find-RS Simplification Procedure

### Input:
- $B$: Set of bins  
- $D$: Set of rules  

### Output:
- $B$: Simplified set of bins  
- $D$: Simplified set of rules  

---

1. **Initialize**:  
   $i \gets 0$

2. **While** $i < \text{len}(D)$:  
   - **For each** $j \in [i+1, \text{len}(D)]$:  
     - $\mathbf{r}' \gets D_j$  
     - $k = 0$  

     - **For each** $\mathbf{p} \in \mathcal{P}$:  
       - **If** $\mathbf{r}' \succeq \mathbf{p}$:  
         - Remove $\mathbf{p}$ from $B_i$  
       - **Else**:  
         - $ k \gets k + 1 $  

   - **If** $D_i$ is empty:  
     - Remove $B_i$  
     - Remove $D_i$  
   - **Else**:  
     - $i \gets i+1$  

3. **Return** $B, D$  

---

## Find-RS Generalization Procedure

### Input:
- $\mathcal{N}$: Set of negative examples  
- $D$: Set of rules  
- $p_{gen}$: Generalization probability (default: 0.9)  

### Output:
- $D$: Generalized set of rules  

---

1. **For each** $D_i \in D$:  
   - $\mathbf{r} \gets D_i$  

   - **For each** $c \in D_i$:  
     - $\mathbf{r}' \gets \mathbf{r} - c$  *// Remove a constraint in a random order*  
     - $p \gets$ random()  
     - **If** $\nexists n \in \mathcal{N} \mid \mathbf{r}' \succeq n \wedge p \leq p_{gen}$:  
       - $\mathbf{r} \gets \mathbf{r}'$  

   - $D_i \gets \mathbf{r}$  

2. **Return** $D$  
