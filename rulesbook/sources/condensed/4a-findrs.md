# Find-RS

Find-RS is a rule learning algorithm that uses a greedy search to find a rule that covers a given example. It is a simple algorithm that can be used to learn a single rule from a dataset. The algorithm is based on the AQ algorithm, which is a rule learning algorithm that uses a separate-and-conquer strategy to learn rules.

A rule set has the best match to a **DNF structure**, since each rule shares the same weight to the others. Moreover, rule sets can be used for concept learning, e.g., finding a set of rules that cover a set of examples (sharing the same class).

## TL;DR

- **Pros:**
  - The base version uses sequential covering to subdivide data into bins, and is simple to understand
  - The extended version leverages the variance of multiple runs to create a more robust classifier (akin to Random Forests)
  - Can be pruned to learn smaller rule sets with importance weights
- **Cons:**
  - Can be slow for large datasets

## Algorithm

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



## Extension to weighted rule sets

![Weighted Find-RS algorithm](find-rs-bp.pdf)

- **Input:**
  - $RS_1, ..., RS_N$: rule sets found by running the algorithm $N$ times

- **Output** 
  - Importance weights for each rule

- Extract each rule in all rule sets
- $R \gets \text{unique}(RS_1, ..., RS_N)$
- Assign a weight to it based on the number of times it appears in the rule sets.
- $W \gets \text{count}(r_1, ..., r_m)$