# Fuzzy Rules

Let $ X $ be the space of possible instances, and $ A $ a fuzzy set defined on $ X $. The membership function of $ A $, denoted $ \mu_A: X \to [0,1] $, assigns to each element $ x \in X $ a degree of membership $ \mu_A(x) $, where:

- $ \mu_A(x) = 1 $ represents full membership,
- $ \mu_A(x) = 0 $ represents non-membership,
- Intermediate values indicate partial membership.

## Fuzzy Thresholding Mechanism

In the context of rule learning, let $ f: X \to [0,1] $ be a feature function that determines the degree to which an instance $ x $ satisfies a given condition. Instead of a binary decision $ f(x) \in \{0,1\} $, we define a fuzzy thresholding mechanism:

$$
d = \mu_A(x) \in [0,1]
$$

where a threshold $ v_t $ defines full coverage ($ d = 1 $), and an upper bound $ v_u $ defines no coverage ($ d = 0 $). The degree of coverage decreases linearly in the interval $ [v_t, v_u] $ according to:

$$
d = \frac{v_u - x}{v_u - v_t}, \quad \text{for } v_t \leq x < v_u
$$

The optimal $ v_u $ is chosen by maximizing a fuzzified precision metric:

$$
\text{precision}^* = \frac{\sum_{x \in P} \mu_A(x)}{\sum_{x \in P \cup N} \mu_A(x)}
$$

where:

- $ P $ and $ N $ denote the sets of positive and negative instances, respectively,
- Each instance contributes to the precision calculation weighted by its membership degree.


## References

* [Fuzzy Sets, Wikipedia](https://en.wikipedia.org/wiki/Fuzzy_set)
* [Foundations of Rule Learning, Furnkranz et al.](https://link.springer.com/book/10.1007/978-3-540-75197-7)