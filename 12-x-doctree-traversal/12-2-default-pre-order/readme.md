
# document traversal / (default) pre-order (PreD)

This chapter provides a brief discussion of the (default) pre-order rule.

* the (default) pre-order rule := `(n × c × s)`
* `trace(n) := n × trace(fc) × ... × trace(lc)`

Note that the resulting total node order is order-preserving.

* it preserves the tree order
* it preserves the child order

Note that the pre-order rule **does not require an order of execution**
since the resulting order (i.e. the pre-order trace) will be the same,
regardless of the order in which the rule is applied.
