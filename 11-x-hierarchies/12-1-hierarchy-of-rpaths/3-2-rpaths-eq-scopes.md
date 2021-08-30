
<!-- ======================================================================= -->
# hierarchy of rpaths <=> hierarchy of scopes

Even though one can first transform any hierarchy of rpaths `HR` into a node
tree `T(N,E)`, and then into a hierarchy of scopes `HS`, one can also directly
transform `HR` into `HS`. Likewise, a direct transformation of `HS` to `HR`
is just as possible.

<!-- ======================================================================= -->
## hierarchy of rpaths => hierarchy of scopes

```
rp(b) := (r  ..  a  ..  b)
         |-------|-------|
          rp(a)    p(a,b)
```

In order to transform HR into HS one needs to recall the general pattern of
the rooted path of a node `b` that has node `a` as an ancestor. That is, each
rooted path `rp(b)` has the rooted path `rp(a)` as a prefix and the path
between `a` and `b` (i.e. `p(a,b)`) as a suffix.

* `rp(b) == (rp(a) \ (a)) × p(a,b)`

Note that `rp(a)` and `p(a,b)` overlap each other in node `a`. To be more
accurate, `(a)` is a suffix to `rp(a)` and a prefix to `p(a,b)`.

Due to the above, and in order to form the scope of node `a` from the rooted
paths in HR, one only needs to form the union of all rooted paths `rp(b)`
that have `rp(a)` as a prefix, and then finally remove all the elements in
the rooted path `rp(a)` without removing `a` itself.

* `HS := { scope(a) | (a in U(HR)) }`
* `scope(a) := (union(a) \ prefix(a)) + {a}`
* `union(a) := { (e in E(s)) | (s in HR) and (a in s) }`
* `prefix(a) := E(rp(a)) := { (e in rp(a)) }`

<!-- ======================================================================= -->
# hierarchy of scopes => hierarchy of rpaths

Recall that each set `(s in HS)` in a hierarchy of scopes `HS` has a unique
rooted path of sets `rp(s)`. In addition to that, each set in `HS` is required
to have one and only one CE which can be understood to represent a node id.
Because of that, `rp(s)` can be transformed such that each element in it is
the CE of the corresponding set. That is, `rp(s)` can be transformed into the
corresponding rooted path of nodes.

* `HR := { rpath(s) | (s in HS) }`
* `rpath(s) := (ce(s1),..,ce(sN))`
* `rp(s) := (s1,..,sN)`
