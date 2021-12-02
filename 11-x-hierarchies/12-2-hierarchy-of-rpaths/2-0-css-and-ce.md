
<!-- ======================================================================= -->
# CSSs and CEs of rooted paths

```
       |-oss(s)=s--------------|
       | |-iss(s)-| |-css(s)-| |
A(s) <---| { .. } | | { .. } |---> D(s)
       | |--------| |--------| |
       |-----------------------|
```

The union of all prefixes `iss(s)` of path `(s in S)`
will be referred to as **the inner subset iss(s)** of path `s`.

* `iss(s) := { e | (e in a) for (a in A(s)) }`

The set difference `css(s)` between a set `s` and its inner subset will be
referred to as **the characteristic subset CSS** of path `s`. That is because
no element in it is an element in any path in `A(s)`. Each element in that
subset will therefore be referred to as **a characteristic element CE**.

* `css(s) := (s \ iss(s))`
* `css: S -> P(U)`

Recall that each rooted path is an ordered set of elements. As such, a rooted
path can be treated as a simple set of elements, just as a subset of the
natural numbers can be treated as a simple set of elements.

As a matter of completeness, the union of a path's characteristic subset css(s)
and its inner subset iss(s) will be referred to as **the outer subset oss(s)**
of path `s`. As such, it is equal to the set of all elements `E(s)` in `s`.

* `oss(s) := (iss(s) + oss(s))`
* `(oss(s) == E(s))` is true

Note that each path `(s in S)` is associated with **a unique CE**, if and only
if each path is required to have a non-empty CSS of size one. Based on that,
the single CE of a CSS will be referred to as **the characteristic element CE**
of the corresponding path.

* `ce(s) := oneOf(css(s))` iff `(#css(s) == 1)`

Recall that a simple setup of rooted paths `S` is required to contain a path
and all of its prefixes. Because of that, each path `(s in S)` is by definition
guaranteed to have one and only one CE.

<!-- ======================================================================= -->
## remarks

* `A*(s) := (A(s) + {s})` and `D*(s) := (D(s) + {s})`

Note that path `s` is the only path in `A*` that has `ce(s)` as an element.
In contrary to that, each path in `D*` has `ce(s)` as an element.

Note that, in contrary to a setup of scopes, `iss(s)` in a setup of rooted
paths contains the root of `s`. That is because the orientations of both types
of setups is converse (i.e. superset-of vs. prefix/subset-of).

* `(#css(s) == 1)` for all `(s in S)`

Note that, since each path `(s in S)` is an ordered sequence, and since `S`
contains `s` and every possible non-empty prefix of `s`, the last element of
each path is the CE of the corresponding path.

* `ce(s) := s[#s]`

Note that, similar to hierarchies of sets, the following functions can be
defined. Also, and since each path in `S` has one and only one CE, `ce(s)`
is inverse to `path-of-ce(e)`, unique and defined for all `(s in S)`.

* ce(), ce-of-path(), path-of-ce()
* css(), css-of-path(), path-of-css()
* ce-of-css(), css-of-ce()

Note that the set of all characteristic elements `CE(S)` is equal to `U(S)`.
That is, each CE is an element in the setup's universal set of elements `U`
and each element in it is the CE of a path.

* `CE(S) := { e | (e in css) for (css in CSS(S)) }`
* `(e in U) <-> (e in CE(S))`
