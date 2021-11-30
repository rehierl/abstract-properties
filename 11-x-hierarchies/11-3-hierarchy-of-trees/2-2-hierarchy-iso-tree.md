
<!-- ======================================================================= -->
# hierarchy of trees <=> node tree

```
node tree       hierarchy of subtrees
=========  <=>  ======================

    1           {   1,   2,   3 ,   4,   5 }
 =======         =======     ===
 2  3  5         2  3  5      4
   ===             ===
    4               4
```

<!-- ======================================================================= -->
## node tree => hierarchy of trees

Given a tree `T(N,E)`, one can form a hierarchy of trees `S` by collecting all
the induced subtrees of that tree - i.e. one induced subtree for each node.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of trees => node tree

Given a hierarchy of trees `S`,
a node tree `T(N,E)` can be formed as follows:

* `T(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(p),r(c)) | (p = p(c)) and (c in S) }`

In words:

* (1) determine the root node `r(t)` of each tree `(t in S)`
* (2) determine the parent tree `p(c)` of each non-root tree `c`
* (3) connect the root node of `p(c)` with the root of its child `c`

Note that the resulting tree has `#S` nodes and that the definition of the
nodes in `T` is provided by the root nodes of each tree `(t in S)`.

Note that each edge `(e in E)` can be seen as the **border edge** between an
induced subtree `T[n]` and any induced subtree `T[a]` that is defined by an
ancestor `(a in A(n))` of node `n`. (see inner-outer-sets).

<!-- ======================================================================= -->
## the node order of a tree

A hierarchy of trees `S` can be used to define a partial order of trees `P`.

* `P(V,<)` where `V := S` and ..
* `(a < t) := (a supertree-of t) and (a != b)`

The order relation `P` of source tree `T` can be formed as follows.

* `P(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(a),r(t)) | (a ancestor-of t) for (a,t in S) }`

Note that this order relation is equal to the source tree's node order. That
is because it can also be derived as the transitive closure of the source
tree's graph. In other words, the transitive reduction of `P` is equal to the
source tree's graph.

Note that each scope of a node `n` can be determined by collecting all of the
sink nodes of node `n`.

* `scope(n) := { d | nEd }`
