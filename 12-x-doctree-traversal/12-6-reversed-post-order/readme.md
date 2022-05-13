
# document traversal / reversed post-order (PostR)

This chapter provides a brief discussion of the reversed post-order rule.

* the reversed post-order rule := `(cR × n × sR)`
* `trace(n) := trace(lc) × ... × trace(fc) × n`

Note that the resulting total node order is not order-preserving.

* it does not preserve the tree order
* it does not preserve the child order

<!-- ======================================================================= -->
## the (postR <=> preD) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace such that both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`

Note that, based on this correspondence, the reversed post-order trace can be
understood to be **(overall) order-reversing**.

* the tree order is reversed
* the child order is reversed
