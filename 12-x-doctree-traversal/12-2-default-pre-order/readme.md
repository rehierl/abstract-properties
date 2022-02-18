
# document trees / (default) pre-order (PreD)

This chapter provides a brief discussion of the default pre-order rule.

* the (default) pre-order rule := `(n × c × s)`
* `trace(n) := n × trace(fc) × ... × trace(lc)`

Note that the resulting total node order is order-preserving.

* preserves the tree order
* preserves the child order

Note that the pre-order rule does not require an order of execution since
the resulting total node order (i.e. the pre-order trace) will be the same,
regardless of the order in which the pre-order rule is applied.

Note that the pre-order trace of a node strongly corresponds with the
**tag-based syntax**. Because of that, a node can be understood to be
**pushed into its start-tag**, which is why the visit of a node corresponds
with its start-tag. In contrary to that, the end-tag of a node is an
end-marker that only marks the end of the node's scope.

* tag-based syntax := `(n × <tag> × c × </tag> × s)`
