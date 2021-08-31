
<!-- ======================================================================= -->
# path-based definitions

<!-- ======================================================================= -->
## level, depth, height

The level/depth of a node can be defined as follows:

* `level(n) := #rp(n)` - the node level of a node
* `level(n)` is the node-length of the node's rooted path
* `depth(n) := (#rp(n) - 1)` - the depth of a node
* `depth(n)` is the edge-length of the node's rooted path
* note - `(level(r) == 1)` but `(depth(r) == 0)`

The height of a node/tree can be defined as follows:

* `height(n) := max({ (#p-1) | p:=(n,..,l) for (l in LN) })`
* `height(n)` is the edge-length of the longest path that
  connects node `n` with a leaf in the corresponding tree
* `height(T) := height(r)` - the height of a tree
* note - `(height(l) == 0)` for `(l in LN)`

Note that the height `height(T)` of a tree `T` is defined as the height
`height(r)` of its root node `r`. As such, the height of a tree is equivalent
to its **diameter**.

<!-- ======================================================================= -->
## peer

A node `x` can be described as a peer to node `y`, if both have the same node
level. Because of that, siblings can be described as peers to each other.

* `x` is a peer to `y`, if `(#rp(x) == #rp(y))`
* `(x peer-to y) := (#rp(x) == #rp(y))`

Note that no node is an ancestor nor a descendant to any of its peers.

<!-- ======================================================================= -->
## ancestor, descendant

The ancestors of a node `n` are those nodes that are presequent to node `n`
in its rooted path `rp(n)`.

* `(a ancestor-of n) := aPn and (a != n)`

The descendants of node `n` are those nodes to which `n` is an ancestor.

* `(d descendant-of n) := nPd and (n != d)`

Note that no node is an ancestor or a descendant to itself.

<!-- ======================================================================= -->
## (sub)sets of nodes

Based paths, the following subsets of `N` can be defined:

* `AN := { a | aPn for some (n in N) }`
* `AN` is the set of all nodes that are ancestors to some node
* `DN := { d | nPd for some (n in N) }`
* `DN` is the set of all nodes that are descendants to some node

With regards to `AN`:

* `AN := (N \ LN)`
* note - `AN` and `LN` are disjoint
* a parent is an ancestor to its child nodes
* a parent may itself have no ancestors - the root

With regards to `DN`:

* `DN := (N \ RN)`
* note - `DN` and `RN` are disjoint
* a child is a descendant to its parent node
* a child may itself have no descendants - a leaf

<!-- ======================================================================= -->
## (helper) functions

A function `(a: N -> P(N))` can be defined
that returns the set of all ancestors of the input node.

* `A(n) := { a | aPn }`
* `(a in A(n)) <-> (a ancestor-of n)`

Likewise, a function `(d: N -> P(N))` can be defined
that returns the set of all descendants of the input node.

* `D(n) := { d | nPd }`
* `(d in D(n)) <-> (d descendant-of n)`

remarks

* `(x ancestor-of n)` is false for each `(x in N\A(n))`
* `(x descendant-of n)` is false for each `(x in N\D(n))`
* `(x related-to n)` is true for each `((x,n) in (A(n)+D(n))×{n})`

<!-- ======================================================================= -->
## distant ancestor/descendant

An ancestor `a` may be referred to as **a distant ancestor** `DA(n)`
of node `n`, if it isn't the parent of `n`.

* `DA(n) := (A(n) \ p(n))`

A descendant `d` may be referred to as **a distant descendant** `DD(n)`
of node `n`, if it isn't a child of `n`.

* `DD(n) := (D(n) \ c(n))`
