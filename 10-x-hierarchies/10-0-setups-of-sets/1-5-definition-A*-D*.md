
<!-- ======================================================================= -->
## remarks - in general

Recall that any ancestor has more elements than any of its descendant.
Likewise, any descendant has fewer elements than any of its ancestors.

* `(#a > #s)` is true for all `(a in A(s))`
* `(#s > #d)` is true for all `(d in D(s))`

Note that, if one focusses on the aspect of "a known fixed rule", then `A(s)`
can be understood to define an induced total sub-setup. Likewise, `D(s)` can
be understood to define an induced partial sub-setup.

<!-- ======================================================================= -->
## subsetups A() and D()

Assuming a **partial setup** `S` and some set `(s in S)` ..

```
                             |-D(s)-partial--|
|-A(s)-total---------|       | |-> .. -> ..  |
| r(s) -> .. -> p(s) |-> s ->|-|-> ..        |
|--------------------|       | |-> .. -> ..  |
                             |---------------|
                               c(s)     l(s)
```

* `A(s)` is a total sub-setup, `D(s)` is a partial sub-setup
* `(r(s) in A(s))` is equal to `max(A(s))` and `r(s)`
* `(p(s) in A(s))` is equal to `min(A(s))` and `p(s)`
* `(c(s) subset-of D(s))` is the set of child sets of `s`
* `(l(s) subset-of D(s))` is the set of leaf sets of `s`

Assuming a **total setup** `S` and some set `(s in S)` ..

```
|-A(s)-total---------|       |-D(s)-total----------|
| r(s) -> .. -> p(s) |-> s ->| c(s) -> .. -> ls(s) |
|--------------------|       |---------------------|
```

* `A(s)` is a total sub-setup, `D(s)` is a total sub-setup
* `(r(s) in A(s))` is equal to `max(A(s))` and `r(s)`
* `(p(s) in A(s))` is equal to `min(A(s))` and `p(s)`
* `(c(s) in D(s))` is equal to `max(D(s))` - the only child of `s`
* `(l(s) in D(s))` is equal to `min(D(s))` - the only leaf of `s`

Note that `A(s)` is always **a total sub-setup**. Because of that, any non-root
set `(s in S)` always has a most significant `r(s) := max(A(s))` and a least
significant `p(s) := min(A(s))` superset.

* `(r(s) == p(s))` for `(s in c(r))` and `(r in RS)`

Note that `D(s)` is in general **a partial sub-setup**. Because of that, there
is in general no least and no most significant subset. However, `D(s)` is a
total sub-setup, if the overall setup is total. Because of that, any partial
setup is always downward-, but not necessarily also upward-total.

Note that the subset of all leaf sets `l(s)` can be described as the subset of
all **minimal sets** in `D(s)` and the subset of all child sets `c(s)` can be
described as the subset of all **maximal sets** in `D(s)`.

<!-- ======================================================================= -->
## extending A/D to A*/D*

```
|-A*-total----------------|  |-D*--partial----|
| r(s) -> .. -> p(s) -> s |  |   |-> .. -> .. |
|-------------------------|  | s-|-> ..       |
                             |   |-> .. -> .. |
                             |----------------|
                                   c(s)  l(s)
```

Since `s` is a subset to each set in `A`, including `s` in `A` results in
a non-empty total sub-setup `A*`. Likewise, since `s` is a superset to each
set in `D`, including `s` in `D` results in a non-empty partial sub-setup
`D*` that may or may not be or total.

* `A*(s) := (A(s)+{s}) := { a | (a ancestor-of s) or (a == s) }`
* `D*(s) := (D(s)+{s}) := { d | (d descendant-of s) or (d == s) }`

Note that, since `s` is included as an element in `A*` and `D*`, both of
these sub-setups are **non-empty**, which otherwise can not be guaranteed
to be the case.

* `(#A* > 0)` and `(#D* > 0)` are both always true

Note that, `D*` is different to `D` isofar as `D` may in general have any
number of roots (aka. maximal sets). In contrary to that, and since `s`
is a superset to each set in `D`, sub-setup `D*` has a greatest set and
therefore **one and only one root**.

* `(#RS(A*) == 1)`, `(#LS(D*) == 1)`
* `(#RS(D*) == 1)`, `(#LS(D*) >= 1)`
