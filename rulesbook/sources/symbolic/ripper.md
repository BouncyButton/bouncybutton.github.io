---
file_format: mystnb
kernelspec:
  name: python3
---

# RIPPER

```{code-cell} python

import ssl

ssl._create_default_https_context = ssl._create_unverified_context

import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from collections import Counter

class RIPPER:
    def __init__(self, max_rules=10, max_conditions=5):
        self.rules = []  # List of (conditions, label)
        self.default_class = None
        self.max_rules = max_rules
        self.max_conditions = max_conditions
    
    def fit(self, X, y):
        df = pd.DataFrame(X)
        df['label'] = y
        
        # Majority class as default rule
        self.default_class = Counter(y).most_common(1)[0][0]
        
        # Generate rules iteratively
        for _ in range(self.max_rules):
            best_rule = self._learn_rule(df)
            if best_rule is None:
                break
            
            self.rules.append(best_rule)
            df = df[~df.apply(lambda row: self._rule_applies(best_rule, row), axis=1)]
            
            if df.empty:
                break
    
    def _learn_rule(self, df):
        best_rule = None
        best_accuracy = 0
        
        for label in df['label'].unique():
            conditions = []
            sub_df = df[df['label'] == label]
            
            for _ in range(self.max_conditions):
                if sub_df.empty:
                    break
                
                best_condition = self._find_best_condition(sub_df)
                if best_condition is None:
                    break
                
                conditions.append(best_condition)
                sub_df = sub_df[sub_df.apply(lambda row: self._condition_applies(best_condition, row), axis=1)]
            
            accuracy = self._evaluate_rule((conditions, label), df)
            if accuracy > best_accuracy:
                best_rule = (conditions, label)
                best_accuracy = accuracy
        
        return best_rule if best_accuracy > 0 else None
    
    def _find_best_condition(self, df):
        best_condition = None
        best_gain = 0
        
        for feature in df.columns[:-1]:
            for value in df[feature].unique():
                condition = (feature, value)
                gain = self._information_gain(condition, df)
                if gain > best_gain:
                    best_condition = condition
                    best_gain = gain
        
        return best_condition
    
    def _information_gain(self, condition, df):
        before = len(df)
        after = len(df[df.apply(lambda row: self._condition_applies(condition, row), axis=1)])
        return before - after  # Simple heuristic: reduce dataset size
    
    def _rule_applies(self, rule, row):
        conditions, label = rule
        return all(self._condition_applies(cond, row) for cond in conditions)
    
    def _condition_applies(self, condition, row):
        feature, value = condition
        return row[feature] == value
    
    def _evaluate_rule(self, rule, df):
        correct = sum(df.apply(lambda row: self._rule_applies(rule, row) and row['label'] == rule[1], axis=1))
        total = sum(df.apply(lambda row: self._rule_applies(rule, row), axis=1))
        return correct / total if total > 0 else 0
    
    def predict(self, X):
        df = pd.DataFrame(X)
        predictions = []
        
        for _, row in df.iterrows():
            matched = False
            for rule in self.rules:
                if self._rule_applies(rule, row):
                    predictions.append(rule[1])
                    matched = True
                    break
            
            if not matched:
                predictions.append(self.default_class)
        
        return np.array(predictions)
```

# Example

```{code-cell} python
from sklearn.metrics import accuracy_score
# get the mushroom dataset
from sklearn.datasets import fetch_openml

data = fetch_openml(name='mushroom')

X = pd.DataFrame(data['data'], columns=data['feature_names'])
y = data['target']

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

ripper = RIPPER(max_rules=10, max_conditions=5)
ripper.fit(X_train, y_train)

y_pred = ripper.predict(X_test)

print(ripper.rules)

accuracy_score(y_test, y_pred)
```

