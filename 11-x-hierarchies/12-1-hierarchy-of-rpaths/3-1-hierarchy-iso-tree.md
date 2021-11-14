
<!-- ======================================================================= -->
# hierarchy of rpaths <=> node tree

```
node tree                rooted paths
==================  <=>  ==============
n1 -|-> n2 -|-> n4       s1: (n1)
    |-> n3  |-> n5       s2: (n1,n2)
                         s3: (n1,n3)
                         s4: (n1,n2,n4)
                         s5: (n1,n2,n5)
```

<!-- ======================================================================= -->
## node tree => hierarchy of rpaths

Given a node tree `T(N,E)`, **a hierarchy of rpaths** `S` can be formed by
collecting the rooted paths of each node in `T`.

* `S(T) := { rp(n) | (n in N(T)) }`

Recall that, in the context of a node tree, the rooted path of an ancestor is
a prefix to the rooted path of a descendant. Because of that, the set of all
rooted paths of a tree `RP(T)` contains a prefix for each rooted path in it.
Also, the rooted path `rp(n)` of any node begins with the tree's root `r` and
ends with the defining node `n`. Because of that, each rooted path has its
defining node as its last element and therefore also as its only
characterisitic element.

* `(ce(s) == n)` is true for `s := rp(n)`

<!-- ======================================================================= -->
## hierarchy of rpaths => node tree

Provided that setup `S` is a hierarchy of rooted paths,
one can form a node tree `T(N,E)` as follows:

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-of b) for (a,b in S) }`

Note that, since each rooted path in `S` is an ordered sequence of nodes, and
therefore isomorphic to a path graph, one an describe the resulting tree `T(N,E)`
simply as the union of path graphs, one for each rooted path in `S`. Based on
that, the universal set `U(S)` is equal to the node tree's set of nodes `N(T)`.

<!-- ======================================================================= -->
## the node order of a tree

A hierarchy of rooted paths `S` can be used to define a partial order `P`.

* `P := (V,<)` where `V := S`
* `(a < b) := (a prefix-of b) and (a != b)`

The order relation `P` of the source tree `T` can be formed as follows.

* `P(N,E)` where `N := { ce(s) | (s in S) }`
* `E := { (ce(a),ce(b)) | (a prefix-of b), (a != b) for (a,b in S) }`
