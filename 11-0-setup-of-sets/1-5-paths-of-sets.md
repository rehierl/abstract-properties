
<!-- ======================================================================= -->
# (rooted) paths of sets

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
* where `(#rp == E(rp))` - an ordered sequence

Note that all rooted paths are **non-empty**. Furthermore, each rooted path
of sets is **an ordered sequence** of sets. Consequently, the rooted path of
each set in a partial setup (T1) is **unique** to it.

Similar to that, **a path** can be formed from set `a` to set `b`
iff one is an ancestor set of the other.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-to rp(b))` is true - i.e. remove a prefix
* `aPb` := true if `p(a,b)` can be formed

<!-- ======================================================================= -->
## path-based definitions

Since paths can be defined in the context of partial setups, path-based
defintions such as the following can be introduced.

* `(a connected-with b)` := true if `aPb` or `bPa`
* `level(s) := #rp(s)` - the level of set `s`
* `depth(s) := (#rp(s) - 1)` - the depth of set `s`
* `height(s) := max({ (#p-1) | p:=(s,..,l) for (l in LS) })`
* `(s peer-to t) := (#rp(s) == #rp(t))`

Note the difference: In the context of node trees, it was essential to first
be able to define paths over the edges of a tree, since one could otherwise
neither provide a definition for "ancestor" nor a definition for "descendant".
