
<!-- ======================================================================= -->
## gemeral remarks

Note that each set `(s in S)` is the union of disjoint subsets (i.e. `css(s)`
and `iss(s)`). Furthermore, the inner subset `iss(s)` of a set can be said to
bind set `s` to its subsets. Likewise, the characteristic subset `css(s)` can
be said to bind set `s` to its supersets. (Hence the arrows in the above
pictogram).

* `(t in D(s)) <-> (t subset-of iss(s))`
* `(t in A(s)) <-> (t superset-of css(s))`

Note that, even though `css(s)` and `iss(s)` may be empty, both can not be
empty at the same time. That is because each `(s in S)` is required to be
non-empty.

* `((#css(s) + #iss(s)) > 0)` must be true for all `(s in S)`
* note - one or both must be non-empty

Note that `CSS(S)` is a union of pairwise disjoint sets. In contrary to that,
`ISS(S)` is a union of related sets. However, ISS is no setup of sets. That is
because `iss(l)` is empty for `(l in LS)`. Despite that, the "DI ex-or RE"
requirement does apply to ISS.

Note that there is in general no requirement as to how many CEs a set in a
setup needs to have. That is, `css(s)` may in general be an empty subset,
a 1-element subset, or a subset of arbitrary size. For reasons elaborated
in a subsequent discussion it is essential to require that each set in a
setup must have a 1-element CSS (i.e. `(#CSS(s) == 1)`) and therefore one
and only one CE.
