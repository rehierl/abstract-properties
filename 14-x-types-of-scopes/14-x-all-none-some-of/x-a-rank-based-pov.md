
<!-- ======================================================================= -->
## a rank-based point of view

```
.. × p × (fs .. ps ..) × n × (fc .. lc ..) × (ns .. ls ..) × ..
                       |-traceO(n)-------------------------|
                       |-traceU(n)---------|-traceO(ns)----|
```

Since the pre-order trace `traceO(ns)` is a suffix to `traceO(n)`, trace
`traceU(n)` can be formed from `traceO(n)` by removing `traceO(ns)` as a suffix.

* `traceU(n) := traceO(n) \ traceO(ns)`

Based on that, and if nodes `n` and `ns` are assumed to be headings of equal
rank, then this removal-based operation can be understood as the formal basis
of rank-based headings. That is, **rank values** can be seen as instructions
to prematurely end open sections. As such, rank values can be said to restrict
default scopes.

* `section(hi) := (tO(hj) \ tO(hj))` if `(rank(hj) >= rank(hi))`

With that in mind, the pre-order trace `tO(hi)` can be seen as the default
scope of heading `hi`, whereas the rank value of heading `hj`, some subsequent
sibling to `hi`, can be understood to prematurely end that scope by removing
its own trace `tO(hj)` (i.e. a suffix) from `tO(hi)`.

Note that, based on the above, a scope can be understood to be forwards
oriented (i.e. along the edges), whereas rank values need to be understood
to be **backwards oriented** (i.e. against the edges).

Since `t(x,y) := tO(x) \ t(y)` will in general not work if `y` is anything but
a subsequent sibling to `x` (WHY ?!?) ...

* the `(\)` must be understood to remove a suffix
* `y` can not be an ancestor to `x` since these are not subsequent to `x`
* `y` can not be a subsequent sibling to `x` since `tO(x)` is then disjoint to `t(y)`
* `y` can not be a descendant of `x` since `(\)` is then, as the removal of a
  suffix, not applicable - i.e. in general not a suffix
* if `(\)` were to be redefined as the removal of a subset, then that would
  tear the section of `x` apart - i.e. it would introduce a gap
* `(\)` can not be redefined to end `x` either way since the other nodes are
  simply not subsequent to `y` - i.e. as an extension to the before
* an attempt to redefine `(\)` in regards to TO will end in a fucking mess
* you would have to move on to `tP()` - has issues of its own

Note that `traceU(n)` acts like the **characteristic element (CE)** to,
or as the **characteristic subset (CSS)** of `traceO(n)`.
