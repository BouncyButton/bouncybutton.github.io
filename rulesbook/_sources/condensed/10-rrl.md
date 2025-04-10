# Rule Representation Learner

The Rule Representation Learner (RRL) is an extension of MLLP. Essentially, it provides:

1. Novel activation functions that work in log-space for numerical stability.
2. A linear layer to learn weighted rules.
3. Skip connections

## Architecture

![RRL architecture](rrl.png)

## Activation functions

The activation functions are defined as follows:

$$
P(v) = \frac{1}{1-\log(v)}
$$

$$
Conj_+(h, W_i) = P( \Pi_{j=1}^n F_c(h_j, W_{i,j}) + \epsilon) \\
Disj_+(h, W_i) = 1 - P( \Pi_{j=1}^n F_d(h_j, W_{i,j}) + \epsilon)
$$