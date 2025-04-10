# Learning rules with backpropagation

The main weaknesses of the previous methods are the ones commonly shared with classic machine learning methods, such as:

1. Need for feature engineering
2. Limited search space
3. Overfitting
4. Limited hierarchical structures

Optimizing rules with common gradient-based optimizers can help to overcome these limitations. Research in this area has
notably been scattered with different notation and keywords, leading to a fragmented landscape.

Most commonly, the methods employ a similar structure to neural networks; nonetheless, they are not.

Generally, a rule is encoded by a single neuron.

1. In a DNN, a neuron usually does not hold any semantic meaning; in rule learning, a neuron represents a rule.
2. In a DNN, a neuron is usually connected to all neurons in the previous layer; in rule learning, a neuron is connected to a subset of neurons in the previous layer.
3. A rule learning method usually provides a discretization of the model, which is not the case in DNNs.

To recap: a neural network:

1. Uses a multilayer structure;
2. Each neuron is connected to all neurons in the previous layer with continuous values;
3. The output is a continuous value;
4. It is optimized with gradient-based methods.
5. Does not provide a discretized representation of the model.

A rule learning method:

1. Uses a multilayer structure;
2. Relaxes the model from a discrete to a continuous representation;
3. It is optimized with gradient-based methods.
4. Each neuron is connected to a **subset** of neurons in the previous layer with binary values;
5. The model can be transformed into a discrete representation.
6. The output is a discrete value.
