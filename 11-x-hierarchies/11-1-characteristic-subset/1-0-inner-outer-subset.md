
<!-- ======================================================================= -->
# (Inner/Outer) subsets of a set

```
       |-oss(s)=s--------------|
       | |-css(s)-| |-iss(s)-| |
A(s) <---| { .. } | | { .. } |---> D(s)
       | |--------| |--------| |
       |-----------------------|
```

The union of all subsets of set `(s in S)` will be referred to as
**the inner subset iss(s)** of set `s`.

* `iss(s) := { e | (e in d) for (d in D(s)) }`
* `iss(s)` is the union of all subsets of `s`

The set difference between a set `s` and its inner subset will be referred to
as **the characteristic subset css(s)** of set `s`. Because of that, no element
in `css(s)` is an element in any set in `D(s)`. Each such element will therefore
be referred to as **a characteristic element (CE)**.

* `(css: S -> P(U))`
* `css(s) := (s \ iss(s))`
* `css(s)` is disjoint to `iss(s)`

Note that `iss(s)` and `css(s)` may both contain any number of elements. That
is, both subsets may be empty, may contain one element only, or may contain
more than one element.

If the characteristic subset `css(s)` has one and only one CE, then that CE
will be referred to as **the characteristic element ce(s)** of set `s`.

* `ce(s) := oneOf(css(s))` iff `(#css(s) == 1)`

As a matter of completeness, the union of a characteristic subset css(s) and
an inner subset iss(s) will be referred to as **the outer subset oss(s)** of
set `s`.

* `oss(s) := (css(s) + iss(s))`
* `(oss(s) == s)` is true

Based on the above, and in regards to a given setup `S`, the following
supersets can be defined ..

* `OSS(S) := S` - all outer sets
* `ISS(S) := { iss(s) | (s in S) }` - all inner sets
* `CSS(S) := { css(s) | (s in S) }` - all characteristic subsets

Note that each set `(s in S)` is associated with **a unique CE** if and only
if each set has a non-empty CSS of size one. Based on that, the single CE of
a CSS will be referred to as **the characteristic element CE** of the
corresponding set.

* `ce(s) := oneOf(css(s))` iff `(#css(s) == 1)`
