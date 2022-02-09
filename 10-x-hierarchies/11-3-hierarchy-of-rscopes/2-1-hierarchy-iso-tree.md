
<!-- ======================================================================= -->
# node tree (T) <=> hierarchy of rscopes (Hrs)

```
node tree                reversed scopes
==================  <=>  ===============
n1 -|-> n2 -|-> n4       s1: {n1}
    |-> n3  |-> n5       s2: {n1,n2}
                         s3: {n1,n3}
                         s4: {n1,n2,n4}
                         s5: {n1,n2,n5}
```

<!-- ======================================================================= -->
## (T => Hrs)

Given a node tree `T(N,E)`, **a hierarchy of rscopes** `S` is formed by first
collecting the rooted paths of each node in `T`. After that, each rooted path
must be replaced by the sets of nodes in it.

* `S(T) := { N(p) | (p in RP(T)) }` where ..
* `RP(T) := { rp(n) | (n in N(T)) }`

Recall that, in the context of a node tree, the rooted path of any ancestor is
a prefix to the rooted path of a descendant. Because of that, the set of all
the rooted paths of a tree `RT(T)` has a prefix for each rooted path in it.

Also, the rooted path `rp(n)` of any node begins with the tree's root `r` and
ends with the defining node `n`. Because of that, each rooted path has its
defining node as its last element and therefore also as its one and only one
characteristic element.

* `rp(n) := (r .. n)`
* `(ce(s) == n)` and `(n == s[#s])` are true for `s := rp(n)`

Due to the above, and once each rooted path `rp(n)` is replaced by its set of
nodes, i.e. the reversed scope `rs(n)` of its defining node `n`, the resulting
set of reversed scopes `S` satisfies the requirements of a hierarchy of rscopes.

<!-- ======================================================================= -->
## (Hrs => T)

Provided that setup `S` is a hierarchy of reversed scopes,
one can derive the node tree `T(N,E)` as follows.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-of b) }`

Recall that a hierarchy of reversed scopes `S` is a family of sets of nodes.
Such a hierarchy therefore has no universal graph `G(S)` associated with it.

<!-- ======================================================================= -->
## order relations

A hierarchy of rscopes `S` can be used to define an order of rscopes `P`.

* `P := (S,<)` where `(a < b) := (a subset-of b) and (a != b)`

The tree order `P` of tree `T` can be formed as follows.

* `P(N,E)` where `N := { ce(s) | (s in S) }`
* and `E := { (ce(a),ce(b)) | (a ancestor-of b) for (a,b in S) }`

Note that this tree order can also be formed from tree `T`.

* `P(N,E)` where `E := { (a,d) | (a ancestor-of d) for (a,d in N) }`
