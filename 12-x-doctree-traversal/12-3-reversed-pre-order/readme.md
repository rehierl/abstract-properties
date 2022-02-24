
# document trees / reversed pre-order (PreR)

This chapter provides a brief discussion of the reversed pre-order rule.
(Recall that the word "reversed" denotes that the child order of a document
tree is reversed/flipped - hence `cR` instead of `c`).

* the reversed pre-order rule := `(n × cR × sR)`
* `trace(n) := n × trace(lc) × ... × trace(fc)`

Note that the resulting total node order is overall not order-preserving.

* it preserves the tree order
* it does not preserve the child order
