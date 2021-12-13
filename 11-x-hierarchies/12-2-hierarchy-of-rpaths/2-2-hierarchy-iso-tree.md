
<!-- ======================================================================= -->
# node tree (T) <=> hierarchy of rpaths (Hrp)

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
## (T => Hrp)

Given a node tree `T(N,E)`, **a hierarchy of rpaths** `S` is formed by
collecting the rooted paths of each node in `T`.

* `S(T) := RP(T) := { rp(n) | (n in N(T)) }`

Recall that, in the context of a node tree, the rooted path of any ancestor is
a prefix to the rooted path of a descendant. Because of that, the set of all
the rooted paths of a tree `RP(T)` has a prefix for each rooted path in it.

Also, the rooted path `rp(n)` of any node begins with the tree's root `r` and
ends with the defining node `n`. Because of that, each rooted path has its
defining node as its last element and therefore also as its one and only one
characterisitic element.

* `rp(n) := (r .. n)`
* `(ce(s) == n)` and `(n == s[#s])` are true for `s := rp(n)`

<!-- ======================================================================= -->
## (Hrp => T)

Provided that setup `S` is a hierarchy of rooted paths,
one can derive the node tree `T(N,E)` as follows.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-of b) }`

Note that, since each rooted path in `S` is an ordered sequence of nodes, and
therefore isomorphic to a path graph, one can describe the resulting tree `T`
as the union of path graphs, one for each rooted path in `S`. Because of that,
the setup's universal graph `G(S)` is equal to the resulting tree `T`.

* `(G(S) == T)` is true

<!-- ======================================================================= -->
## order relations

A hierarchy of rpaths `S` can be used to define an order of rpaths `P`.

* `P := (S,<)` where `(a < b) := (a prefix-of b) and (a != b)`

The tree order `P` of tree `T` can be formed as follows.

* `P(N,E)` where `N := { ce(s) | (s in S) }`
* and `E := { (ce(a),ce(b)) | (a ancestor-of b) for (a,b in S) }`
* note - `ce(s) := s[#s]`

Note that this tree order can also be formed from tree `T`.

* `P(N,E)` where `E := { (a,d) | (a ancestor-of d) for (a,d in N) }`
