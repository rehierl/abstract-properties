
<!-- ======================================================================= -->
# child order

As mentioned before, any tree `T(N,E)` is defined as a tuple of a set of nodes
`N` and a set edges `E` over `N×N`. Based on that, any parent `p` in a tree
can be understood to be associated with a simple set of child nodes `c(p)`
that can be formed from `E`.

* `c(p) := { c | pEc }`
* `(a sibling-of b) := (pEa and pEb)`

Because of that, and strictly based on the above mathematical definition,
**no tree can be described as having a child order**.

However, due to the limitations of real world applications, trees can only be
processed one node at a time. A tree can therefore be understood to have an
ordered sequence over its nodes associated with it (aka. **a trace of nodes**),
which contains all the nodes of a tree in the order in which each node needs
to be processed.

* `trace(T), t(T) := (n1,..,nZ)`
* `(#t == #N)` is true

Since `t` is an ordered sequence over a tree's set of nodes `N`, any child of
a parent can be understood to have a unique index associated with it. Based
on that trace of nodes, a parent can be understood to have a first child and
a last child, and thus a child order associated with it.

**The child order of a parent CO(p)** can be defined as an induced subsequence
of (i.e. a total suborder to) the tree's trace of nodes, induced by the parent's
set of child nodes. As such, the child order of a parent can be described as
"an ordered sequence of child nodes" and as **an ordered sequence of siblings**.

* `CO(p) := t[c(p)] := (c1,..,cZ)`
* `(#t[c(p)] == #c(p))` is true

Note that `CO(p)` is not required to be a substring to `t`.

**The child order of a tree CO(T)** can be defined as a set of non-empty child
orders, one for each parent node in it. More accurately, the child order of a
tree is a set of ordered sequences of siblings.

* `CO(T) := { t[c(p)] | (p in PN) }`

Note that the child order of a parent is disjoint to the child order of any
other parent. As such, the child order of a tree can be described as a forest
of (total) child orders.

Note that, if a child order is associated with a tree, then a child order is
associated with all of its parent nodes. That is, there is no tree such that
some parents have a child order, while others do not. Put differently, either
all parent nodes have a child order exor none at all.

<!-- ======================================================================= -->
## the cover relation of a child order

Since the child order of a parent node can be described as an induced ordered
sequence of siblings, a parent node can be understood to be associated with
an order relation that formalizes its child order. That is, for a parent node
`p` and its ordered sequence of child nodes `CO(p) := (c1,..,c2)` one can
define the cover relation `R(p)` of its order relation as follows:

* `R(p) := CO(V,E)` where `V := c(p)` and ..
* `E := { (a,b) | (a next-presequent-to b) }`
* `(a next-presequent-to b) := (idx(a) == idx(b)-1)`
* note - `idx()` is in regards to `CO(p)`

Note that `R(p)` is a cover relation since its set of edges is not transitive.
Despite that, and as a matter of convenience, subsequent discussions will treat
such cover relations as being synonymous to the order relation of a parent's
child order.

Due to the above, the child order `R(T)` of a tree `T(N,E)` can also be defined
as the cover relation of an order relation:

* `R(T) := CO(V,E)` where `V := CN(T)` and ..
* `E := { e | (e in R(p)) for (p in PN(T)) }`

That is, a tree which has a child order associated with it can be described
as being accompanied by a cover relation such that it contains an edge for
each pair of adjacent siblings.

Note that it is these edges that must be embedded into the tree order of an
unordered doctree.

<!-- ======================================================================= -->
## first/last/next/previous sibling

Given the order relation `R(p)` of a parent's child order,
the following definitions can be made:

* `(c first-child-of p)` := there is no sibling `s` such that `sRc`
* `(c last-child-of p)` := there is no sibling `s` such that `cRs`
* `(s next-sibling-of c) := cRs` and `(s previous-sibling-of c) := cRs`

Assuming an indicator function `aPb` such that it is true if a path can be
formed over the edges in `R`, the following definitions can be made:

* `(a presquent-sibling-of b) := aPb`
* `(a subsequent-sibling-of b) := bPa`

Note that the **next sibling** `s` of a child `c` is such that there is no
other sibling `t` subsequent-to `c` and also presequent-to `s`. That is,
based on the child order, there is no other sibling in between `c` and `s`.
Because of that, `s` can also be described as the **next-subsequent** sibling.

Note that the **previous sibling** `s` of a child `c` is such that ther is
no other sibling `t` presequent-to `c` and also subsequent-to `s`. That is,
based on the child order, there is no other sibling in between `s` and `c`.
Because of that, `s` can also be described as the **next-presequent** sbiling.

<!-- ======================================================================= -->
## semantical considerations - can be ignored

```
child order CO(p)      cover graph
=================  =>  ====================
(c1,c2,c3,c4)          c1 -> c2 -> c3 -> c4
```

Since the order relation of a child order CO(p) can be said to have the
**presequent-sibling-of** semantics associated with it, and since the order
relation of a node tree T(N,E) can be said to have the **ancestor-of**
semantics, one first needs to resolve the issue with seemingly incompatible
semantics.

However, since the child order of a parent can be understood to be defined
in terms of an ordered sequence of child nodes, one can also define the child
order of a parent in terms of **a path graph**. Consequently, and since each
path graph is also **a node tree**, the **ancestor-of** semantics can be said
to also apply to the child order of a parent.

* `(c1 presequent-sibling-of c4) <=> (c1 ancestor-of c4)`

Furthermore, and since the terms "sibling" and "ancestor" are such that one
in general associates a particular meaning with them, and based on that also
certain expectations, one should recall that the generic edge-based semantics
still apply. That is, the "ancestor-of" semantics is still synonymous to the
**presequent-to** semantics. To be more clear, "presequent-sibling-of" and
"ancestor-of" can both be said to be defined based on the generic edge-based
"presequent-to" semantics.

* `(c1 presequent-sibling-of c4) := (c1 presequent-to c4)`
* `(c1 ancestor-of c4) := (c1 presequent-to c4)`

Because of that, one should **ignore these semantical considerations** since
they do not define the relationships between the nodes. They are only used
to describe them using specific terms.