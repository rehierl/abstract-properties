
<!-- ======================================================================= -->
# path-based definitions (2)

<!-- ======================================================================= -->
## inner/outer nodes of a node

Due to all rooted paths having a downward (aka. inward) directed orientation,
the nodes in `N` can be classified in regards to a given node `n`:

The set of descendants `D(n)` of a node `n` be referred to as
**the set of inner nodes of a node** `IN(n)`. That is, each descendant
is understood as an inner node in regards to `n`. Based on that, a node
can be understood to support a notion of "inside".

* `IN(n) := D(n)`
* note - `(n !in ON(n))`

Since each node can be understood to have an "inside", any node can conversely
also be understood to have an "outside". The set of nodes that are not inner
nodes to a given node, excluding the node itself, can therefore be said to be
**the set of outer nodes of a node** `ON(N)`.

* `ON(n) := (N \ IN(n) \ {n})`
* note - `(n !in IN(n))`

Note that not every outer node is also an ancestor of `n`.
Also, no node is considered "inside" and "outside" to itself.

* `(A(n) subset-of ON(n))`

<!-- ======================================================================= -->
## contains, inside-of, outside-of

A node `x` can be said to **contain** node `y`,
if `(y in IN(x))`. That is, `y` is an inner node of `x`.

* `(y in x), (x contains y) := (y in IN(x)) := xPy`

A node `x` is can be said to be **(located) inside of** node `y`,
if `(x in IN(y))`. That is, `x` is an inner node of `y`.

* `(x inside-of y) := (x in y)`
* `(x inside-of y) <-> (IN(x) subset-of IN(y))`

A node `x` can be said to be **(located) outside of** node `y`,
if `(x in ON(y))`. That is, `x` is an outer node of `y`.

* `(x outside-of y) := (x in ON(y))`

Note that both definitions (i.e. inside-of, outside-of) provide some sense of
orientation/direction (i.e. inwards, outwards) in regards to a given node.

<!-- ======================================================================= -->
## coupled, disjoint, overlap

Two distinct nodes `x` and `y` can be said to be **coupled** with each other,
if one contains the other. That is, one node is an inner node (aka. a descendant)
of the other.

* `(x coupled-with y) := (xPy or yPx)`
* note - "coupled-with" has no orientation

Two distinct nodes `x` and `y` can be said to be **disjoint** to/from each
another, if both nodes are not coupled with each other. Because of that,
two disjoint nodes have no descendant in common (e.g. siblings).

* `(x disjoint-to y) := not (x coupled-with y)`
* `(x disjoint-to y) <-> (IN(x) disjoint-to IN(y))`
* note - disjoint-to has no orientation

Note that, if `(y in x)` is true, then any descendant `d` of `y` is also a
descendant of `x`. That is because any rooted path `rp(d)` contains `x` and
`y` such that `(x presequent-to y)`. Therefore, `(d in IN(x))` is true for
all `(d in IN(y))`. Consequently, `(IN(y) strict-subset-of IN(x))` is true
because `y` is also a descendant of `x`, but no descendant to itself.

Because of that, two sets of inner nodes `IN(x)` and `IN(y)` in a tree are
either strictly related (i.e. one is a strict subset of the other) ex-or both
sets are disjoint. As such these sets have no nodes in common. Consequently,
there is no pair of nodes in a tree possible that can be understood to overlap
each other - i.e. **no overlap**.
