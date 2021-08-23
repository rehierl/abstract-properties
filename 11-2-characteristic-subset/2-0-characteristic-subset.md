
<!-- ======================================================================= -->
# The characteristic subset - css(s)

```
|-A-------|   |-C-----------|
| 1 |-B-| |   | |-D-| |-E-| |
|   | 2 | |   | | 1 | | 2 | |
|   |---| |   | |---| |---| |
|---------|   |-------------|
```

* /A={1,2}, /A/B={2}
* css(/A)={1}, css(/A/B)={2}
* /C={1,2}, /C/D={1}, /C/E={2}
* css(/C)=Ø, css(/C/D)={1}, css(/C/E)={2}

The **characteristic subset css(s)** of set `s` in a partial setup (T1)
`S` is such that no element in it is also an element of any descendant
`(d in D(s))`.

* `(css: S -> P(U))`
* `css(s) := (s \ iss(s))` where ..
* `iss(s) := { e | (e in d) for (d in D(s)) }`

With that in mind, the set of all characteristic subsets `CSS(S)`
and the set of all inner sets `ISS(S)` can be defined.

* `OSS(S) := S` - all outer sets
* `CSS(S) := { css(s) | (s in S) }` - all characteristic subsets
* `ISS(S) := { iss(s) | (s in S) }` - all inner sets

<!-- ======================================================================= -->
## (css(s) in S)

The CSS of a leaf set `(l in LS)` is equal to `l` and as such a set in `S`.

That is because a leaf set has no descendant set which could result in the
removal of an element. Also, the CSS of a leaf set is always non-empty since
all sets in `S` are required to be non-empty.

* `(l in LS) <-> (css(l) in S)`
* `(l in LS) -> (css(l) == l)`
* `(l in LS) -> (#css(l) > 0)`

<!-- ======================================================================= -->
## (css(s) not-in S)

The CSS of a parent set `(p in PS)` may be empty.
That is because, if a parent set `p` is equal to the union of its child sets,
then all the elements in `p` are also elements in its subsets and as such
elements in its inner subset `iss(s)`.

* `(#css(p) == 0) <-> (p == iss(p))`
* `(#css(p) == 0) -> (p in PS)`

In that particular case, parent set `p` must have more than one child set.
That is because `p` would otherwise be equal to his then only child set.

* `(#css(p) == 0) -> (#c(p) > 1)`

The CSS of a parent set `(p in PS)` is no set in `S`.

That is obviously true if `css(p)` is empty since no set in `S` is allowed to
be empty. However, it is also true if `css(p)` is non-empty. That is because
`p`, as a parent set, must have one or more non-empty child sets, which is why
the then non-empty CSS of `p` is guaranteed to have fewer elements than `p`.

Hence, and in order for `(css(p) in S)` to be true, `css(p)` would have to be a
descendant set of `p`. (Recall that in a hierarchy, coupled sets are strictly
related to each other). However, `css(p)` can by definition not be a descendant
set of `p` since `css(p)` would then have to be empty. And because `css(p)` can
not be empty and non-empty at the same time, `css(p)` is no set in `S`.

* `(p in PS) <-> (css(p) not-in S)`

Note that the codomain of `css()` can not be changed from `P(U)` to `S`
since `(CSS(S) \ S)` is guaranteed to be non-empty if `(#PS > 0)`.

<!-- ======================================================================= -->
## CSS(S), disjoint, unique

```
|----------------|
| s1    s2    s3 | - S
|--\----/-----|--|
    \  /      |
|----\/-------|--|
| c1=c2=Ø     c3 | - CSS(S)
|----------------|
```

Two distinct sets in `S` may have the same CSS.
That is because `css(p)` may be empty for more than one `(p in PS)`.

* `CSS-to-S` is in general a `1:N` relationship
* `(#CSS(S) < #S)` may be true

Any element in `css(s)` is unique to it. That is, `CSS(S)` is a set of
**pairwise disjoint** sets and as such a partition of `U(S)`. Consequently,
no two sets have the same non-empty CSS. Because of that, each non-empty
`css(s)` is **unique** to `s`.

(1) For two distinct sets `(s,t in S)` to have coupled characteristic subsets,
sets `s` and `t` would have to intersect each other (i.e. `((s & t) != Ø)`).
That is because `css(s)` is still a subset of `s` and `css(t)` is still a
subset of `t`.

(2) In order for `(s & t)` to be non-empty, sets `s` and `t` would have to be
related with each other. That is because two distinct sets in a partial setup
are required to be disjoint ex-or related.

(3) If `(t in S)` is a descendant of `(s in S)`, then `css(s)` can not have
any element in `t` and therefore also no element in `css(t)`. That however is
in conflict with (1) since `(css(s) & css(t))` would then be empty. Because of
that, two distinct sets in `S` can not have coupled non-empty characteristic
subsets.

* `(css(s) disjoint-to css(t))`, if `(s != t)`
* `css(s)` is unique to `s`, if `(#css(s) > 0)`

Note that, if each set `(s in S)` has a non-empty CSS, then the set of all
characteristic subsets `CSS(S)` has `#S` elements.

* `(#CSS(S) == #S)` iff `(#css(s) > 0)` for all `(s in S)`
* i.e. `CSS-to-S` is a `1:1` relationship
