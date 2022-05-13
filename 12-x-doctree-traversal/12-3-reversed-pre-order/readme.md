
# document traversal / reversed pre-order (PreR)

This chapter provides a brief discussion of the reversed pre-order rule.

* the reversed pre-order rule := `(n × cR × sR)`
* `trace(n) := n × trace(lc) × ... × trace(fc)`

Note that the resulting total order is not overall order-preserving.

* it preserves the tree order
* it does not preserve the child order

Recall that the word **reversed** denotes that the child order of a document
tree is reversed/flipped - hence `cR` and `sR` instead of `c` and `s`.

<!-- ======================================================================= -->
## the (preR <=> postD) correspondence

Note that the reversed pre-order trace corresponds with the default post-order
trace. That is because both traces are reversed to each other.

* `preR(n) := n × (lc .. fc ..)`
* `postD(n) := (.. fc .. lc) × n `
* `preR(T)` is reversed to `postD(T)`
