
# document traversal / (default) pre-order (PreD)

This chapter provides a brief discussion of the (default) pre-order rule.

* the (default) pre-order rule := `(n × c × s)`
* `trace(n) := n × trace(fc) × ... × trace(lc)`

Note that the resulting total order is (overall) order-preserving.

* it preserves the tree order
* it preserves the child order

Note that the pre-order rule **does not require an order of execution** since
the resulting order will be the same, regardless of to which node the ruled
is applied first.

Note that the pre-order rule can be described as **well-defined**. That is,
a set of edges can be pre-determined from the ordered document tree.

* `E := { e(n) | (n in N) }` where `e(n) := (lc(n),ns(n))`
* `lc(n)` the node's current last child
* `ns(n)` the node's current next sibling

<!-- ======================================================================= -->
## the (preD <=> postR) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace. That is because both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`
