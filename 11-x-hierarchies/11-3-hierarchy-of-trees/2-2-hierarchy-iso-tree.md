
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

Given a tree `T(N,E)`, one can form a hierarchy of trees `S` by collecting
all the induced subtrees of that tree - i.e. one induced subtree per node.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of trees => node tree

Given a hierarchy of trees `S`,
a node tree `T(N,E)` can then be formed as follows.

* `T(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(p),r(c)) | (p = p(c)) and (c in S) }`

In words:

* (1) determine the root node `r(t)` of each tree `(t in S)`
* (2) determine the parent tree `p(c)` of each non-root tree `c`
* (3) connect the root node of `p(c)` with the root node of its child `c`

Note that the resulting tree has `#S` nodes and that the definition of the
nodes in `T` is provided by the root nodes of each tree `(t in S)`.

Note that each edge `(e in E)` corresponds with the **border edge** between
an induced subtree `T[c]` and its parent tree `T[p]`. (see inner-outer-sets).

<!-- ======================================================================= -->
## derived order relations

A hierarchy of trees `S` can be used to define an order of trees `P`.

* `P(S,<)` where `(a < t) := (a supertree-of t) and (a != b)`

The tree order order relation `P` of tree `T` can be formed as follows.

* `P(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(a),r(d)) | (a ancestor-of d) for (a,d in S) }`

Note that this order relation can also be formed from tree `T`.

* `P(N,E)` where `E :=  { (a,d) | (a ancestor-of d) for (a,d in N) }`
