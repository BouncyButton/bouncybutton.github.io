---
file_format: mystnb
kernelspec:
  name: python3
---


# Units for learning rules with backpropagation

Many (sometimes equivalent) choices have been employed to learn propositions with backpropagation.

A neuron can encode the following:

1. Membership for a fixed logical
   operation [Payani et al., 2018](https://arxiv.org/pdf/1904.01554), [Wang et al.](https://arxiv.org/abs/2310.14336)
2. A choice between a set of logical operations [Petersen et al., 2022](https://arxiv.org/pdf/1906.03523).

Advantages/disadvantages of the first choice are:

1. The structure is always the same; it is arguably more efficient due to vectorized operations.
2. It can be less expressive; we are forced to use a fixed set of operations (commonly AND, OR, sometimes XOR).
3. When considering a large amount of literals, the gradient can vanish (e.g., with product operations).

Advantages/disadvantages of the second choice are:

1. The structure is more flexible.
2. It can be less efficient.
3. It can be more expressive.

Let's see some examples.

## Membership for a fixed logical operation

Let's define a simple, continuous operation that can be used to encode whether a literal should be included.

$$
F_c(x_i, m_i) = 1 - m_i \cdot (1 - x_i) = 1 - m_i + m_i \cdot x_i
$$

This operation has a nice interpretation, as it can also be seen as the fuzzy implementation of the S-implication in its
Reichenbach/product version [Van Krieken et al., 2022](https://arxiv.org/pdf/2002.06100).

$$
a \rightarrow_{RC} c \equiv I_{RC}(a,c) = 1 - a + a \cdot c \equiv m_i \rightarrow_{RC} x_i
$$

Note that both the input $x_i \in [0,1]$ and the membership $m_i \in [0,1]$ are bounded. Usually $m_i$ is bounded by either a sigmoid ($\sigma = \frac{1}{1 + e^{-x}}$) or a HardTanh ($\text{HardTanh}(x) = \max(0, \min(1, x))$) function.

Let's see how this operation behaves.

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt

def F_c(x_i, m_i):
    return 1 - m_i + m_i * x_i

xx, yy = np.linspace(0, 1, 100), np.linspace(0, 1, 100)
X, Y = np.meshgrid(xx, yy)
Z = F_c(X, Y)

plt.contourf(X, Y, Z, levels=100)
plt.xlabel('x_i')
plt.ylabel('m_i')
plt.title('F_c(x_i, m_i)')

plt.colorbar()

plt.show()
```

Payani et al. also define a $F_d$ function, which can be traced back to the same implication.

$$
F_d(x_i, m_i) = x_i \cdot m_i
$$

## Logical operations

To encode logical operations, authors have used the following operations:

1. AND: $F_{AND}(a, b) = a \cdot b$ [Payani et al., 2018](https://arxiv.org/pdf/1904.01554), [Wang et al.](https://arxiv.org/abs/2310.14336), [Petersen et al., 2022](https://arxiv.org/pdf/1906.03523)
2. OR: $F_{OR}(a, b) = a + b - a \cdot b = 1 - (1-a) \cdot (1-b)$ [Payani et al., 2018](https://arxiv.org/pdf/1904.01554), [Wang et al.](https://arxiv.org/abs/2310.14336)