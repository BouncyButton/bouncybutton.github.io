# Layers for learning rules with backpropagation

The main building block for handling many rules at once is the layer. A layer is a collection of neurons that are connected to the previous layer.

Mathematically:

$$ f_L : \mathbb{R}^{m} \rightarrow \mathbb{R}^{n} $$

where $m$ is the number of neurons in the previous layer and $n$ is the number of neurons in the current layer.

The implementation differs depending on the method. The most common choice is to do as follows:

$$
Conj(h, W_i) = \prod_{j=1}^n F_c(h_j, W_{i,j})
$$

In this way, we encode into a $W \in \mathbb{R}^{m \times n}$ matrix all the membership values for the $m$ input values into the $n$ hidden neurons.