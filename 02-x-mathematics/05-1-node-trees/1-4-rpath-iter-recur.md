
<!-- ======================================================================= -->
# rooted paths

Note that the following needs to be understood to point out the connection
between node trees and node orders. As such, it can be seen as an easy to
understand "first point of contact". (Like dipping your toe into icy water).

<!-- ======================================================================= -->
## a recursive point of view

In a rooted path, any edge is downward oriented (i.e. from an ancestor
towards its descendants). Because of that, the ancestors `A(n)` of a
node `n` are all presequent to that node in the node's rooted path:

* `E(rp(n)) == (A(n) union {n})`
* `rp(n) := (prefix × n)` where `(E(prefix) == A(n))`
* `(rp(a) prefix-of rp(n))` where `(a ancestor-of n)`

Furthermore, the parent `p` of a node is considered the least significant
ancestor of a node. That is, `p` is subordinate to every other ancestor
in `A(n)`:

* `rp(n) := (prefix × p × n)` where `(E(prefix) == DA(n))`
* `rp(n) := (rp(p) × n)` where `(p parent-of n)`

The root `r` of a tree is the most significant ancestor to each node in it.

* `(r ancestor-of n)` is true for all non-root nodes `(n in N\RN)`

<!-- ======================================================================= -->
## an iterative point of view

Recall that with each non-root node `n` of a tree `T(N,E)` a set of ancestors
`A(n)` is associated. That is, each node in `A` is considered an ancestor of
`n`, which is why `n` is a descendant to each node in `A`. Because of that,
`n` can be described as being least significant to each node in `A`.

Since no node in a tree has more than one parent, and since eac node in
`A` is related to every other node in it, `A` is guaranteed to have a least
significant node `l` such that it is a descendant to each node in `A\l`.
Because of that, `l` is the parent node of `n`, and `A\l` contains all the
ancestors of `l`.

* `(l == p(n))` is true
* `(A(l) == A(n)\{l})` is true

One can therefore imagine an iterative process which subsequently removes the
next least significant node from `A` until the only node that remains in `A`
is the trees root `r(n) := r` (to which `n` is a descendant). Because of that,
`r` is the most significant ancestor to each node in `A(n)` and consequently
also to every other node in `N`.

* for `(a ancestor-of d)` ..
* `(r(a) == r(d))`, but `(p(a) != p(d))`
* `(p(a) ancestor-of p(d))`

<!-- ======================================================================= -->
## a trace of sets

Due to the above, the iterative process is guaranteed to end.

* `A(0) := A(n)+{n}`
* note - `(l0 == n)`
* `A(i+1) := (Ai \ li)`
* note - `(A(i+1) == A(li))`
* note - `li` is the parent of `l(i-1)`
* `(A(N) == { r(n) })`

As such the iterative process can be understood to produce
an ordered sequence of sets of nodes `s`.

* `s := (A(0),..,A(N))`
* `(s(i) superset-of s(j))` if `(i < j)`
* `(s(i) related-to s(j))` is true for any `(i,j in [1,#s])`
* note - `(i,j in S)` is equivalent to `({i,j} subset-of S)`

Such a trace of sets can thus be used to define an order `P(V,<)`
over the sets of sets `E(s)` in `s`.

* `P(V,<)` where `V := E(s)` and ..
* `(a < b) := (a superset-of b)`
