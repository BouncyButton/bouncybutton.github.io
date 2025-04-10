# Multilayer Logical Perceptron

The Multilayer Logical Perceptron ([Wang et al., 2021](https://drive.google.com/open?id=1uMuaQpDvZoXAMkl6fGUscGUTXsQR9rCf&amp;usp=drive_fs)) essentially expands the
previous baseline with the following:

1. A way to get a **discrete representation** of the rules. (Concept Rule Sets)
2. Methods to overcome **vanishing gradients**. (Random Binarization)

## Concept Rule Sets

![MLLP](mllp.png)

A concept rule set is used to get back a discrete representation of the rules. Essentially, weights are binarized using a threshold.

$$
\text{binarize}(w) = \begin{cases}
1 & \text{if } w \geq \theta \\
0 & \text{otherwise}
\end{cases}
$$

The threshold $\theta$ is fixed to 0.5. Other algorithmic techniques are employed (dead node detection, redundant rules elimination).

## Random Binarization

The authors observe vanishing gradients (possibly due to the presence of products). To address this, they propose a random binarization method to learn rules more effectively. Essentially, the weights are binarized randomly during training.

$$
\tilde{w} = \begin{cases}
binarize(w) & \text{with probability } p \\
w & \text{with probability } 1 - p
\end{cases}
$$