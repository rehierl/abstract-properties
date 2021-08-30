
<!-- ======================================================================= -->
# CSSs and CEs of rooted paths

```
       |-oss(s)=s--------------|
       | |-iss(s)-| |-css(s)-| |
A(s) <---| { .. } | | { .. } |---> D(s)
       | |--------| |--------| |
       |-----------------------|
```

The union of all prefixes of path `(s in S)` will be referred to as
**the inner subset iss(s)** of path `s`.

* `iss(s) := { e | (e in a) for (a in A(s)) }`
* `iss(s)` is the union of all prefixes of `s`

The set difference between a set `s` and its inner subset will be referred
to as **the characteristic subset css(s)** of path `s`. Because of that, no
element in `css(s)` is an element in any path in `A(s)`. Each such element
will therefore be referred to as **a characteristic element (CE)**.

* `(css: S -> P(U))`
* `css(s) := (s \ iss(s))`

As a matter of completeness, the union of a path's characteristic subset css(s)
and its inner subset iss(s) will be referred to as **the outer subset oss(s)**
of path `s`.

* `oss(s) := (iss(s) + oss(s))`
* `(oss(s) == E(s))` is true

Note that each path `(s in S)` is associated with **a unique CE**, if and only
if each path is required to have a non-empty CSS of size one. Based on that,
the single CE of a CSS will be referred to as **the characteristic element CE**
of the corresponding path.

* `ce(s) := oneOf(css(s))` iff `(#css(s) == 1)`

<!-- ======================================================================= -->
## remarks

Note that `s` is the only path in `A*` that has `ce(s)` as an element.
In contrary to that, each path in `D*` has `ce(s)` as an element.

* `(#css(s) == 1)` for all `(s in S)`

Note that, since each path `(s in S)` is an ordered sequence, and since `S`
contains `s` and every possible non-empty prefix of `s`, any path in `S` is
guaranteed to have a CSS of size 1. Because of that, the last element of each
path is the CE of the corresponding path.

* `ce(s) := s[#s]`

Note that, based on the above, the following functions can be defined. Also,
and since each path in `S` has one and only one CE, `ce(s)` is inverse to
`path-of-ce(e)`, unique and defined for all `(s in S)`.

* ce(), ce-of-path(), path-of-ce()
* css(), css-of-path(), path-of-css()
* ce-of-css(), css-of-ce()

Note that the set of all characteristic elements `CE(S)` is equal to `U(S)`.
That is, each CE is an element in `U` and each element in `U` is a CE in some
CSS.

* `CE(S) := { e | (e in css) for (css in CSS(S)) }`
* `(e in U) <-> (e in CE(S))`
