
<!-- ======================================================================= -->
# paths of sets

```
|-A*-total-/-rp(s)--------|
| r(s) -> .. -> p(s) -> s |
|-------------------------|
```

Since each set in `A*` has a unique amount of elements, which is monotone
decreasing from `r(s)` to `s`, the sets in `A*` can be used to define the
**rooted path** `rp(s)` of set `s` as an ordered sequence of sets, ordered
in decreasing order of signinficance.

* `rp, rp(s) := (s1..sN)` such that `(si in A*(s))`
* where `(rp[i] superset-of rp[j])` for `(i < j)`
* where `(#rp[i] > #rp[i+1])` for `(i in [1,#rp-1])`

Note that all rooted paths are **non-empty** since each rooted path ends in
set `s`. Furthermore, each rooted path is **an ordered sequence** of sets.
Also, the rooted path of a set in a partial setup is **unique** to it.

Based on the definition of rooted paths, **a path** can be formed from set
`a` to set `b` if set `a` is an ancestor of `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` if `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` is true if `p(a,b)` can be formed

<!-- ======================================================================= -->
## path-based definitions

Since paths can be formed in the context of a partial setup of sets,
path-based defintions such as the following can be introduced.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(s) := #rp(s)` - the level of set `s`
* `depth(s) := (#rp(s) - 1)` - the depth of set `s`
* `height(s) := max({ (#p-1) | p:=(s,..,l) for (l in LS) })`
* `(s peer-to t) := (#rp(s) == #rp(t))`

Note the difference: In the context of node trees, it was essential to first
be able to define paths over the edges of a tree. That is because one could
otherwise neither provide a definition for "ancestor", nor a definition for
"descendant". In contrary to that, the definition of both terms is based on
the specific definition of the related-to operator.
