# Gradient-based optimization for rule-based models

As we discussed so far, two main ingredients are essential for finding a rule-based model:

1. Defining the **structure** (and thus the search space) of models.
2. Defining a suitable **optimizer** to search a good model.

The following works, in one way or another, essentially revisit the second point, by relaxing the representation of rules in a **continuous space** and enabling gradient-based optimization. This is a significant departure from the previous works, as it allows for a more flexible search space, but also introduces new challenges, such as the need for a differentiable model.

This idea comes with many advantages:
* **Deep representations come for free**: the model can learn intermediate representations by exploiting backpropagation.
* **Scalability**: the model can be trained with large datasets, thanks to the efficiency of gradient-based optimization.
* **Modularity**: gradient-based architectures can be potentially integrated with other models, such as neural networks.