---
file_format: mystnb
kernelspec:
  name: python3
---

# Architectures

Broadly speaking, the literature has focused on extracting **flat** structures or **deep** structures. Let's see a possible, differentiable, implementation.

## Problem

Let's consider a simple problem where at least three out of four binary features should be true in order to classify an instance as positive. Let's define a common training procedure.

```{code-cell} python

d = 8

def train(model):
    # train on a simple dataset: abc or bcd or abd; e is irrelevant
    import numpy as np
    from itertools import product
        
    X = list(product([0, 1], repeat=d))
    y = np.array([(int(x[0] and x[1] and x[2]) or (x[1] and x[2] and x[3]) or (x[1] and x[2] and x[3])) for x in X])
    
    from sklearn.model_selection import train_test_split
    
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
    
    X_train = torch.tensor(X_train, dtype=torch.float32)
    y_train = torch.tensor(y_train, dtype=torch.float32)
    
    X_test = torch.tensor(X_test, dtype=torch.float32)
    y_test = torch.tensor(y_test, dtype=torch.float32)
    
    train_dl = torch.utils.data.DataLoader(torch.utils.data.TensorDataset(X_train, y_train), batch_size=32)
    
    
    criterion = torch.nn.BCELoss()
    
    optimizer = torch.optim.Adam(model.parameters(), lr=0.01)
    
    for epoch in range(1000):
        for X_train, y_train in train_dl:
            optimizer.zero_grad()
            output = model(X_train)
            loss = criterion(output, y_train.unsqueeze(1))
            loss.backward()
            optimizer.step()
        if epoch % 100 == 0:
            print(f'Epoch {epoch} loss {loss.item()}')
    
    # test
    with torch.no_grad():
        output = model(X_test)
        loss = criterion(output, y_test.unsqueeze(1))
        print(f'Test loss {loss.item()}')
```

## Flat

The flat architecture is the easiest case. As shown by [Dierckx et al.](https://drive.google.com/open?id=18akcNVRNoqxx8NseHrJtVaweINshC0hh&usp=drive_fs), [Wang et al.](https://arxiv.org/abs/2310.14336), [Beck and Furnkranz](https://drive.google.com/open?id=1GUHn_Imi_Z2o6F8EwK6ymTpCY_vJP1BJ&usp=drive_fs) you can express a set of rules by using a CNF-based or a DNF-based representation. This translates in having an AND layer, and a OR layer, and deciding which one to process first.

```{code-cell} python
:tags: [scroll-output]

import torch


class AndLayer(torch.nn.Module):
    def __init__(self, n_inputs, n_outputs):
        super(AndLayer, self).__init__()
        self.weights = torch.nn.Parameter(torch.rand(n_inputs, n_outputs))
        # self.clip = torch.nn.Hardtanh(0, 1)
        self.clip = torch.nn.Sigmoid()

    def forward(self, x):
        w = self.clip(self.weights)
        # return torch.prod(1. - (1. - x) * w, dim=1)
        # i want to get for each x_i and for each z_j, z_j = 1 - (1 - x_i) * w_ij
        return torch.prod(1. - (1. - x).unsqueeze(2) * w, dim=1)


class OrLayer(torch.nn.Module):
    def __init__(self, n_inputs, n_outputs):
        super(OrLayer, self).__init__()
        self.weights = torch.nn.Parameter(torch.rand(n_inputs, n_outputs))
        self.clip = torch.nn.Hardtanh(0, 1)

    def forward(self, x):
        w = self.clip(self.weights)
        # return 1. - torch.prod(1 - x @ w, dim=1)
        return 1. - torch.prod(1 - x.unsqueeze(2) * w, dim=1)


and_layer = AndLayer(d, 2 * d)
or_layer = OrLayer(2 * d, 1)

model = torch.nn.Sequential(and_layer, or_layer)

train(model)
```

## Deep

Now, a deep architecture is simply the result of the stacking of multiple layers. In this case, we can use the same layers as before.

```{code-cell} python
:tags: [scroll-output]

and_layer1 = AndLayer(d, 2 * d)
or_layer1 = OrLayer(2 * d, d)
and_layer2 = AndLayer(d, 2 * d)
or_layer2 = OrLayer(2 * d, 1)

model = torch.nn.Sequential(and_layer1, or_layer1, and_layer2, or_layer2)

train(model)
```
