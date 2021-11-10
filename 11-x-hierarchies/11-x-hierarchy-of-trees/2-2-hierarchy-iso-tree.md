
<!-- ======================================================================= -->
# hierarchy of trees <=> node tree

```
node tree       hierarchy of subtrees          node tree
=========  <=>  ========================  <=>  =========

    1           {   1,  2,  3 , 4, 5}              1
 =======         =======   ===                  =======
 2  3  5         2  3  5    4                   2  3  5
   ===             ===                            ===
    4               4                              4
```

<!-- ======================================================================= -->
## node tree => hierarchy of trees

Given a tree `T(N,E)`, one can form a hierarchy of trees `S` by collecting
all the induced subtrees of that tree - i.e. one tree for each node in `T`.

* `S := { T[n] | (n in N) }`
* `(#S == #N)` is true

<!-- ======================================================================= -->
## hierarchy of trees => node tree

Given a hierarchy of of trees `S`, one can recreate the source tree `T(N,E)`
as follows: (1) determine the root node `r(t)` of each tree `(t in S)`,
(2) determine the parent tree `p(t)` of each non-root tree `t`, and finally
(3) create an edge `(e in E)` such that it connects the root node of `p(t)`
with the root node of its child tree `t`.

* `T(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(p),r(t)) | (p = p(t)) and (t in S) }`

Note that the resulting tree has `#S` nodes and that the definition of the
nodes in `T` is provided by the root nodes of each tree `(t in S)`.

Note that the edges `(e in E)` are the **border edges** between an induced
subtree `T[n]` and all of the induced subtrees `T[a]` that are defined by
the nodes ancestors `(a in A(n))`. (see inner-outer-sets).

<!-- ======================================================================= -->
## the node order of a tree

A strict partial order of trees `P` can be formed just as easily.

* `P(S,<)` where `(a < t) := (a ancestor-of t)`
* note - `(a ancestor-of t) := (a supertree-of t)`

The order relation `P` of the tree order of the source tree `T`
can be formed as follows.

* `P(N,E)` where `N := { r(t) | (t in S) }`
* `E := { (r(a),r(t)) | (a ancestor-of t) }`

Note that this order relation directly reflects the actual
node order of tree `T`.

Note that this order relation is isomorphic to the source tree `T`. That is
because each scope of a node `a` can be easily determined by collecting all
the sink nodes in `E` of node `a`.

* `scope(a) := { d | aEd }`

Note that the reflexive transitive reduction of this order relation is equal
to the relation/graph of source tree `S`.
