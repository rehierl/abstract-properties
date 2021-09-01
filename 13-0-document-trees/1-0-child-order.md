
<!-- ======================================================================= -->
# child order

As mentioned before, any tree `T(N,E)` is defined as a tuple of a set of
nodes `N` and a set edges `E` over `N×N`. Based on that, any parent `p`
in a tree can be understood to be associated with a simple set of child
nodes `c(p)` which can be derived from `E`.

* `c(p) := { c | pEc }`
* `(a sibling-of b) := (pEa and pEb)`

Because of that, and strictly based on the mathematical definition,
**no tree can be described as having a child order**.

However, due to the limitations of real world programs, trees can only be
processed one node at a time. A tree can therefore be understood to have
an ordered sequence of nodes associated with it (aka. **a trace of nodes**),
which contains all the nodes of a tree in the order in which each node was
processed.

* `trace(T), t(T) := (n1,..,nZ)` where `(Z == #N)`
* `(#t == #N)` and `(E(t) == N)` are both true

Since `t` is an ordered sequence over a tree's set of nodes `N`, any child
of a parent can be understood to have a unique index associated with it.
Because of that, the child nodes of a parent will be processed one child
at a time. That is, a parent can be understood to have a first child and
a last child.

**The child order of a parent co()** can be defined as an induced total
suborder to the tree's trace of nodes, induced by the parent's set of child
nodes. As such, the child order of a parent can be described as "an ordered
sequence of child nodes" and as **an ordered sequence of siblings**.

* `CO(p) := t[c(p)] := (c1,..,cZ)` where `(Z == #c(p))`
* note - `(E(co) == c(p))` where `co := t[c(p)]`
* note - `c(p)` is empty, if `p` is no parent node

**The child order of a tree CO()** can be defined as a set of non-empty
child orders, one for each parent node in it. More accurately, the child
order of a tree is a set of ordered sequences of siblings.

* `CO(T) := { t[c(p)] | (p in N) }`

Note that the child order of a parent is disjoint to the child order of any
other parent. As such, the child order of a tree can be described as a forest
of (total) child orders.

Note that, if a child order is associated with a tree, then a child order is
associated with all of its parent nodes. That is, there is no tree such that
some parents nodes have a child order, while other parent nodes do not. Put
differently, either all parent nodes have a child order exor none at all.

<!-- ======================================================================= -->
## the order relation of a child order

Since the child order of a parent node can be described as an induced ordered
sequence of siblings, a parent node can be understood to be associated with
an order relation that formalizes its child order. That is, for a parent node
`p` and its ordered sequence of child nodes `CO(p) := (c1,..,c2)` one can
define the order relation `R(p)` of a parent's child order as follows:

* `R(p) := CO(V,E)` where `V := c(p)` and ..
* `E := { (a,b) | (a next-presequent-to b) }`
* `(a next-presequent-to b) := (co[a] == co[b]-1)`
* `co[n]` returns the index of `n` in `co`

Note that the order relation `CO` is not transitive and therefore, strictly
speaking, not an actual order relation. However, this endo-relation can still
be turned into an actual order relation by simply adding all the missing
transitive edges - i.e. by performing a transitive closure. Put differently,
the relation as defined above is the cover relation/graph of the actual order
relation of a child order.

Based on that, one can describe each parent node as having a simple set of
edges associated with it - i.e. `E(p)`. Consequently, the child order `R(T)`
of a tree `T(N,E)` can also be described as an order relation:

* `R(T) := CO(V,E)` where `V := CN(T)` and ..
* `E := { e | (e in CO(p)) for (p in CN(T)) }`

That is, a tree that has a child order associated with it can be described
as being accompanied by such an order relation such that it contains an edge
for each pair of adjacent siblings.

Note that it is these edges that must be embedded into an unordered doctree.

<!-- ======================================================================= -->
## first/last/next/previous sibling

Given the order relation `R(p)` of the child order of a parent `p`,
the following definitions can be made:

* `(c first-child-of p)` := there is no sibling `s` such that `sRc`
* `(c last-child-of p)` := there is no sibling `s` such that `cRs`
* `(s next-sibling-of c) := cRs` and `(s previous-sibling-of c) := cRs`

Note that the **next sibling** `s` of a child `c` is such that there is no other
sibling `t` subsequent-to `c` and also presequent-to `s`. That is, according to
the corresponding child order, there is no other sibling in between `c` and `s`.
Based on that, `s` can also be described as the **next-subsequent** sibling.

Note that the **previous sibling** `s` of a child `c` is such that ther is no
other sibling `t` presequent-to `c` and also subsequent-to `s`. That is, and
according to the child order, there is no other sibling in between `s` and `c`.
Based on that, `s` can also be described as the **next-presequent** sbiling.

<!-- ======================================================================= -->
## presequent/subsequent sibling

Given the order relation `R(p)` of the child order of a parent `p`,
and an indicator function `aPb` such that it is true if a path can
be formed over `R`, then the following definitions can be made:

* `(a presquent-sibling-of b) := aPb`
* `(a subsequent-sibling-of b) := bPa`

Note that, in regards to these definitions, is it probably easier to think
in terms of ordered sequences of siblings (hint - the index order).
