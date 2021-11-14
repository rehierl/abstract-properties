
<!-- ======================================================================= -->
# hierarchy of trees <=> node tree

```
node tree       hierarchy of subtrees
=========  <=>  ======================

    1           {   1,  2,  3 , 4, 5 }
 =======         =======   ===
 2  3  5         2  3  5    4
   ===             ===
    4               4
```

<!-- ======================================================================= -->
## node tree => hierarchy of trees

Given a tree `T(N,E)`, one can form a hierarchy of trees `S` by collecting
all the induced subtrees of that tree - i.e. one tree for each node in `T`.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of trees => node tree

Assumed that setup `S` is a hierarchy of trees,
one can form a node tree `T(N,E)` as follows:

* `T(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(p),r(t)) | (p = p(t)) and (t in S) }`

In words:

* (1) determine the root node `r(t)` of each tree `(t in S)`
* (2) determine the parent tree `p(t)` of each non-root tree `t`
* (3) connect the root node of `p(t)` with the root of its child `t`

Note that the resulting tree has `#S` nodes and that the definition of the
nodes in `T` is provided by the root nodes of each tree `(t in S)`.

Note that the edges `(e in E)` are the **border edges** between an induced
subtree `T[n]` and all of the induced subtrees `T[a]` that are defined by
the nodes ancestors `(a in A(n))`. (see inner-outer-sets).

<!-- ======================================================================= -->
## the node order of a tree

A hierarchy of trees `S` can be used to define a partial order of trees `P`.

* `P(V,<)` where `V := S` and ..
* `(a < t) := (a supertree-of t) and (a != b)`

The order relation `P` of the source tree `T` can be formed as follows.

* `P(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(a),r(t)) | (a ancestor-of t), (a != t) for (a,t in S) }`

Note that this order relation is isomorphic to the source tree `T`. That is
because each scope of a node `a` can be determined by collecting all the sink
nodes of node `a`.

* `scope(a) := { d | aEd }`

Note that the reflexive transitive reduction of this order relation is equal
to the relation/graph of source tree `S`.
