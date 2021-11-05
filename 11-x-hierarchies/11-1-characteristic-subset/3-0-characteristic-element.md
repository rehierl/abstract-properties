
<!-- ======================================================================= -->
# Characteristic element (CE)

```
|-------------|
| c1={}    c2 | - CSS(S)
|---------/|--|
         / |
|-------/--|--|
|      e1  e2 | - CE(S)
|-------------|
```

Any element in a CSS can be described as **a characteristic element CE**.
Based on that, one can form the union of all characteristic elements `CE(S)`
by simply forming a set over all the elements in each CSS.

* `CE(s) := css(s)` for `(s in S)`
* `CE(css) := css` for `(css in CSS(S))`
* `CE(S) := { e | (e in css) for (css in CSS(S)) }`
* note - the union of all characteristic elements in `S`

Note that, depending on a given context, `(s in S)` and `css(s)`
may both be described as "the parent set" of any `(ce in css(s))`.

Note that **any CE is unique to its CSS**.
That is because `CSS(S)` is a union of pairwise disjoint sets.

* any CE is a CE of one and only one CSS
* no CE can be a CE of more than one CSS

Note that this "uniqueness" is similar to the "uniqueness" of a CSS. That
is, the parent set of a CSS is the least significant set that has a given
CE as its CE.

<!-- ======================================================================= -->
## CE(S) = U

The set of all characteristic elements `CE(S)` is equal to `U`. That is, each
CE is an element in `U` and each element in `U` is a CE in some CSS.

* `(e in U) <-> (e in CE(S))`
* `(CE(S) == U)` is true

(0) Each CE is an element in a CSS and as such an element in a set of `S`.
And since `U` is the union of all sets in `S`, each CE is an element in `U`.

(1) Any non-empty partial setup `S` has by definition one or more root sets in
`RS`. Furthermore, and since any non-root set is a subset to a root set, any
element in `(e in U)` is an element in such a root set.

(2) If `(e in U)` is the element of a root set `(r in RS)` such that it is no
element to a subset of `r`, then `e` is a characteristic element of `r` (i.e.
`(e in css(r))` is true). In that case, `e` has been identified as a CE.

(3) If `(e in U)` is no CE to a root set, then `e` must also be an element in
one and only one of its child sets. That is due to the DI-RE requirement of a
partial setup.

(4) The child set `(c in S)` can now be seen as the "current root `r`" of a
partial sub-setup (i.e. `(c -> r)`). Because of that, the iteration continues
with step-2 until `(e in U)` is the CE of the current root.

Note that the iteration is guaranteed to end. That is because a child set has
fewer elements than its parent set, which is why the iteration either ends with
a parent set `p` such that `(e in css(p))` ex-or with a leaf set `(l in LS)`
such that `(e in css(l))`.
