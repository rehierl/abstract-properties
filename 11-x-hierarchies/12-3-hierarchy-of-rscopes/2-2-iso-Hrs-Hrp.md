
<!-- ======================================================================= -->
# hierarchy of rscopes (Hrs) <=> hierarchy of rpaths (Hrp)

Even though one can first transform a hierarchy of reversed scopes Hrs into a
node tree `T(N,E)`, and then that tree into a hierarchy of rooted paths Hrp,
a direct transformation of Hrs into Hrp is possible. Likewise, a direct
transformation of Hrp into Hrs is possible.

<!-- ======================================================================= -->
## (Hrp => Hrs)

Recall that the set of nodes of a rooted path `rp(n)` is equal to the reversed
scope `rs(n)` of its defining node `n`. Because of that, Hrs can be formed from
Hrp by simply replacing each rooted path by its set of nodes.

* `Hrs(Hrp) := { N(p) | (p in Hrp) }`

<!-- ======================================================================= -->
## (Hrs => Hrp)

Assuming that a hierarchy of reversed scopes Hrs was formed from a hierarchy
of rooted paths Hrp as described above, Hrp can be formed from Hrs by first
collecting all the rooted paths `RP(Hrs)` of reach reversed scope. After that,
one only needs to replace each reversed scope in each path in `RP()` by its
characteristic element CE.

* `RP(Hrs) := { rp(s) | (s in Hrs) }`
* `replace(s): (s1..sk) -> (ce(s1)..ce(sk))`
* `Hrp(Hrs) := { replace(s) | (s in RP(Hrs)) }`

<!-- ======================================================================= -->
## remarks

Since Hrp holds the rooted path of a node `rp(n)` and also the rooted path
`rp(a)` of any ancestor `a` of `n`, Hrp can be said to embed the total
subhierarchy `Hrp(n)` of rooted paths, which contains a rooted path for
each node in `A*(n)` over the corresponding source tree.

* `Hrp(p) := A*(p)` where `p := rp(n)`
* note - `A*(p)` contains `p` and all of its prefixes in `Hrp`

The subhierarchy `Hrp(p)` is, as a hierarchy of rooted paths, isomorphic to a
tree, which happens to be the path graph of the rooted path `rp(n)` over the
source tree `T`. Because of that, replacing each rooted path in `Hrp(p)` by
its set of nodes results in a total hierarchy of reversed scopes `Hrs(s)`
that is isomorphic to the very same tree.

* `Hrs(s) := A*(s)` where `s := rs(n)`
* note - `A*(s)` contains `s` and all of its subsets in `Hrs`

Recall that each rscope in `Hrs(s)` has its defining node as its one and only
characteristic element. Furthermore, that subhierarchy is total, which is why
the rooted path of rscopes `rp(s)` of the reversed scope `rs(n)` corresponds
with that hierarchy. That is, the set of elements of the rooted path of rscopes
`rp(s)`, which is an ordered sequence of rscopes, is identical to `Hrs(s)`.

* `( #Hrs(s) == #rp(s) )` where `s := rs(n)`
* `( Hrs(s) == E(rp(s)) )` is true
