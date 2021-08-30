
<!-- ======================================================================= -->
# hierarchy of rpaths <=> node tree

```
(a next-presequent-to b)       S := +si
========================  <=>  ==============
n1 --|-> n2 --|-> n4           s1: (n1)
     |-> n3   |-> n5           s2: (n1,n2)
                               s3: (n1,n3)
                               s4: (n1,n2,n4)
                               s5: (n1,n2,n5)
```

Recall that, in the context of a node tree, the rooted path of an ancestor is
a prefix to the rooted path of a descendant. Because of that, `RP(T)` contains
a prefix for each rooted path in it. Also, the rooted path `rp(n)` of any node
begins with the tree's root `r` and ends with the given node `n`. Because of
that, each rooted path has its defining node as its last element and therefore
also as its only characterisitic element.

* `(ce(s) == n)` for `s := rp(n)`

<!-- ======================================================================= -->
## node tree => hierarchy of rpaths

Given a node tree `T(N,E)`, **a hierarchy of rpaths** `S` can be formed by
simply collecting all the rooted paths of each node in `T`. That hierarchy
of paths can then be used to form a strict partial order `P(S,<)` using either
the "prefix-of" or the "subset-of" operator as the basis of the order operator.

* `P := (V,<)` such that `(V := RP(T))`
* `S := { rp(n) | (n in N(T)) }`
* `(a < b) := (a prefix-of b) and (a != b)`

Note that the partial order `P` is order maintaining:

* `(a ancestor-of b) <-> (rp(a) prefix-of rp(b))`

<!-- ======================================================================= -->
## hierarchy of rpaths => node tree

Provided that a given setup `S` is a hierarchy of rooted paths,
one can form a node tree `T(N,E)` as follows:

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-of b) for (a,b in S) }`
