
<!-- ======================================================================= -->
# overall remarks

Note that the length-based encoding scheme is **an implicit encoding scheme**
since it doesn't directly encode the edges of a tree.

Recall that the extended set of nodes in `D*(n)` can be described as the open
interval `[n,*]` over the unordered document tree (DTU). Because of that, the
**number of nodes** in these sets is equal to the length of the pre-order trace
`pre(n)`. Hence, the description as a "length-based" rather than a "size-based"
or a "count-based" encoding.

Note that the length-based encoding does not allow to define cycles. That is,
the structure of a graph that is defined using the length-based encoding is
guaranteed to be **acyclic**. That is because, the string defined by the
length-value of a node `n` can only be a substring to, or overlap the string
defined by the length-value of a presequent node `a`. That is, it is not
possible to define a superstring since node `n` would then also have to be
presequent to `a`, which simply isn't possible.

Recall the reason in regards to containment orders:
No set can be a superset and also a subset to another set.
