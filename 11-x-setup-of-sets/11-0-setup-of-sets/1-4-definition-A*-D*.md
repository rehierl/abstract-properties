
<!-- ======================================================================= -->
## remarks - in general

Note that any ancestor set has more elements than any of its descendant sets.
Likewise, any descendant set has fewer elements than any of its ancestor sets.

* `(#a > s)` is true for any `(a in A(s))`
* `(s > #d)` is true for any `(d in D(s))`

Note that a partial setup has **no cycles**. That is because no set can be a
subset and also a superset to another set. It would need to have fewer and also
more elements than the other set. Because of that, the set of ancestor and
descendant sets are disjoint.

* `(A(s) disjoint-to D(s))` is true

<!-- ======================================================================= -->
## remarks - (sub)setup

Assuming a **partial setup** `S` and a set `(s in S)` ..

```
                             |-D(s)-partial--|
|-A(s)-total---------|       | |-> .. -> ..  |
| r(s) -> .. -> p(s) |-> s ->|-|->           |
|--------------------|       | |-> .. -> ..  |
                             |---------------|
                                   c(s)  l(s)
```

* `A(s)` is a total sub-setup, `D(s)` is a partial sub-setup
* `(r(s) in A(s))` is equal to `max(A(s))` - root set
* `(p(s) in A(s))` is equal to `min(A(s))` - parent set
* `(c(s) subset-of D(s))` a set of child sets - child sets
* `(l(s) subset-of D(s))` a set of leaf sets - leaf sets

Assuming a **total setup** `S` and a set `(s in S)` ..

```
|-A(s)-total---------|       |-D(s)-total----------|
| r(s) -> .. -> p(s) |-> s ->| c(s) -> .. -> ls(s) |
|--------------------|       |---------------------|
```

* `A(s)` is a total sub-setup, `D(s)` is a partial sub-setup
* `(r(s) in A(s))` is equal to `max(A(s))` - root set
* `(p(s) in A(s))` is equal to `min(A(s))` - parent set
* `(c(s) in D(s))` is equal to `max(D(s))` - child set
* `(l(s) in D(s))` is equal to `min(D(s))` - leaf set

Note that `A(s)` is always **a total sub-setup**. Because of that, any non-root
set `(s in S)` always has a most significant `r(s) := max(A(s))` and a least
significant `p(s) := min(A(s))` **superset**.

* `(r(s) == p(s))` for `(s in c(r))` and `(r in RS)`

Note that `D(s)` is in general **a partial sub-setup**. Because of that, there
is in general no least/most significant subset in it. However, the subset of
all leaf sets `l(s)` can be described as the subset of all **minimal sets** in
`D(s)` and the subset of all child sets `c(s)` can be described as the subset
of all **maximal sets** in `D(s)`.

Note that each parent set in a total setup must have **one child set only**.
( That is because if a parent set had more than one child set, then the setup
would have a pair of unrelated/incomparable sets. As such, the setup would not
be a total setup ). Consequently, each parent set in a total setup always has
a least `l(p)` and a most significant **subset** `c(p)`. Any non-empty total
setup therefore has **exactly one root and excatly one leaf set**.

<!-- ======================================================================= -->
## extending A/D to A*/D*

```
|-A*-total----------------|  |-D*--partial----|
| r(s) -> .. -> p(s) -> s |  |   |-> .. -> .. |
|-------------------------|  | s-|->          |
                             |   |-> .. -> .. |
                             |----------------|
                                   c(s)  l(s)
```

Since `s` is a subset to each set in `A`, adding `s` to the sub-setup `A`
will still result in a total sub-setup `A*`. Similar to that, adding `s`
to the sub-setup `D` will still result in a sub-setup `D*` that is either
partial or total.

* `A*, A*(s) := A(s) + {s} := { a | (a ancestor-of s) or (a == s) }`
* `D*, D*(s) := D(s) + {s} := { d | (d descendant-of s) or (d == s) }`

Note that, since `s` is added as an element to `A` and `D`, both of these
sub-setups are **always non-empty**.

* `(#A* > 0)` and `(#D* > 0)` are both true

Note that, `D*` is different to `D` isofar as `D` may in general have any
number of root sets (aka. maximal sets). In contrary to that, and since
`s` is a superset to each set in `D`, the sub-setup `D*` has a greatest
set and therefore **one and only one root set**.

* `(#RS(A*) == 1)`, `(#LS(D*) == 1)`
* `(#RS(D*) == 1)`, `(#LS(D*) >= 1)`
