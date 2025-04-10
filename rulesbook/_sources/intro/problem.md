# Problem statement

Historically, rule learning systems essentially operate by learning *boolean functions*, which are defined as follows:

$$
c: X \rightarrow \{0, 1\}^k
$$

where $X$ is the input space and $k$ is the number of classes. The output of the function is a binary vector of length \(k\), where each element corresponds to a class. 

Most rule learning methods opt to run a *binarization* step which converts the inputs to a binary representation. 

$$
c = f \circ b : X \rightarrow \{0,1\}^d \rightarrow \{0,1\}^k

f : \{0,1\}^d \rightarrow \{0,1\}^k

b : X \rightarrow \{0,1\}^d
$$

where $f$ is the rule learning algorithm and $b$ is the binarization step, also called *binarizer*. We will denote as $d \in \mathbb{N}$ the dimensionality of the input space extracted by the binarizer.

The reasons for this two-step process are threefold:

1. Historical: initial rule learning approaches employ symbolic solvers that require a binary representation of the data. 
2. Computational: the binarization step allows for the use of efficient data structures and algorithms to represent and manipulate the data.
3. Interpretability: the binarization step allows to extract representations that are sparse and understandable.

