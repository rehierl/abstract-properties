
# document traversal / (default) post-order (PostD)

This chapter provides a brief discussion of the (default) post-order rule.

* the (default) post-order rule := `(c × n × s)`
* `trace(n) := trace(fc) × ... × trace(lc) × n`

Note that the resulting node order is not overall order-preserving.

* it does not preserve the tree order
* it preserves the child order

<!-- ======================================================================= -->
## the (preR <=> postD) correspondence

Note that the reversed pre-order trace corresponds with the default post-order
trace. That is because both traces are reversed to each other.

* `preR(n) := n × (lc .. fc ..)`
* `postD(n) := (.. fc .. lc) × n `
* `preR(T)` is reversed to `postD(T)`
