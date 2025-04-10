# Deep Rule Network Classifier

A Deep Rule Network Classifier ([DRNC](https://arxiv.org/abs/2106.10254), Furnkranz & Beck, 2021), is a rule-based model that attempts to learn deep representations of rules. They observe that one of the main strengths of neural networks is learning **intermediate representations**, and for rule learning this has not been really explored.
Their experiments show that learning with no gradient-based search is possible, albeit does not work as well as RIPPER. The main issue is the much wider search space of the model, which makes it harder to find a good solution, thus heuristics are needed. 

## TL;DR

- **Pros**:
  - One of the few methods which attempt to learn deep representations using a non-gradient search algorithm.
  - Convergence is guaranteed.
- **Cons**:
  - Still does not work well (scalability, performance)
  - Works on binary features only.

## Motivating example

Learning the parity concept using unstructured models is a challenging task (left). Leveraging intermediate representations can help in learning the concept in a more compact way (right).

![DRNC](drnc-parity.png)

This is translated into a learnable architecture, where red connections are ANDs, and green connections are ORs.

![DRNC](drnc-network.png)


## Algorithm

The algorithm essentially explores via a mini-batch strategy the full dataset, and flips the connections in the network to fit each minibatch. This is essentially an hill-climbing search in a discrete space (that can get stuck to a local optima).

- **Input:**
  - $\text{drnc}$: DRNC model
  - $x$: Input features
  - $y$: Target labels
  - $\text{batch_size}$: Size of each batch for optimization

- **Output:**
  - $\text{drnc}$: The trained DRNC model

- **Initialization:**
  - $\text{drnc.initialize()}$
  - $n_{\text{samples}} \gets \text{length}(x)$
  - $n_{\text{batches}} \gets \frac{n_{\text{samples}}}{\text{batch_size}}$
  - $\text{best_accuracy} \gets \text{accuracy_score}(y, \text{drnc.predict}(x))$
  - $\text{best_coefs} \gets \text{drnc.coefs}$

- **For each epoch $e \gets 0$ to $n_{\text{epochs}} - 1$:**
  - $x, y \gets \text{shuffle}(x, y)$
  
  - **For each batch $b \gets 0$ to $n_{\text{batches}} - 1$:**
    - $x_{\text{mb}}, y_{\text{mb}} \gets \text{next_batch}(\text{batch_size})$
    - $\text{coefs} \gets \text{drnc.optimize_coefs}(x_{\text{mb}}, y_{\text{mb}})$
    - $\text{accuracy} \gets \text{accuracy_score}(y, \text{drnc.predict}(x))$
    - **If $\text{accuracy} > \text{best_accuracy}$:**
      - $\text{best_accuracy} \gets \text{accuracy}$
      - $\text{best_coefs} \gets \text{drnc.coefs}$

- **After completing the training loop:**
  - $\text{drnc.coefs} \gets \text{best_coefs}$
  - $\text{drnc.optimize_coefs}(x, y)$

- **Return:**
  - $\text{drnc}$


## Optimizing Coefficients

- **Input:**
  - $\text{drnc}$: Deep Rule Network model
  - $x$: Input features
  - $y$: Target labels
  - $\text{best_accuracy}$: Best observed accuracy

- **Output:**
  - $\text{coefs}$: Optimized coefficients

- **Initialization:**
  - $\text{best_accuracy}, \text{flip_count} \gets 0$
  - $\text{optimal} \gets \text{false}$

- **While $\neg \text{optimal} \wedge \text{flip_count} < \text{drnc.max_flips}$:**
  - **For each layer $i$:**
    - **For each node $j$ in layer $i$:**
      - **For each connection $k$:**
        - Flip $\text{drnc.coefs}[i][j][k]$
        - $\text{accuracy} \gets \text{accuracy_score}(y, \text{drnc.predict}(x))$
        - **If $\text{accuracy} > \text{best_accuracy}$:**
          - Update $\text{best_accuracy}, \text{best_coefs}, i, j, k$
        - Flip back $\text{drnc.coefs}[i][j][k]$
        
  - **If $\neg \text{optimal}$:**
    - Flip $\text{drnc.coefs}[i][j][k]$
    - Update $\text{best_accuracy}, \text{best_coefs}$
    - $\text{flip_count} \gets \text{flip_count} + 1$

- **Return:**
  - $\text{coefs}$

