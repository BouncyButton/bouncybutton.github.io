# RIPPER

RIPPER (Repeated Incremental Pruning to Produce Error Reduction) is a rule learning algorithm that builds a list of rules from data.

- Uses **sequential covering**.
- Prunes rules to avoid overfitting.


## TL;DR

* **Pros:**
  * Essentially still SOTA for rule learning
  * It is reasonably fast for smaller datasets, mature, and provides interpretable models.
* **Cons:**
  * Limited to rule list structures.
  * Guided by the quality measure heuristic.
  

## Sequential covering

(from https://christophm.github.io/interpretable-ml-book/rules.html)

![Sequential covering](covering-algo-1.png)


## Algorithm

* Start with an empty list of rules (rlist).
* Learn a rule $r$
* While the list of rules is below a certain quality threshold (or positive examples are not yet covered):
  * Add rule $r$ to rlist.
  * Remove all data points covered by rule $r$
  * Learn another rule on the remaining data.
* Return the decision list.
