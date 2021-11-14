
<!-- ======================================================================= -->
# Further definitions

As before, the following will focus on the most notable definitions only.
Because of that, the following provides core path-based counterparts of
set-based definitions.

<!-- ======================================================================= -->
## (induced) subsetup

A subset of a setup can be described as **a sub-setup**.
Likewise, a superset of a setup can be described as **a super-setup**.

In the context of a setup of paths **an induced sub-setup** `S[r]` is such
that it contains the specified path as a root, and all the other paths in
`S` to which `r` is a prefix.

* `S[r], S[r,*] := { s | (r prefix-of s) or (s == r) }`

Note that the induced subsetup can still be understood such that it
**grows with the orientation** of the corresponding setup, not against it.
That is because the subsetup grows with the orientation of the prefix-of
relationship.

Note that this definition fo "induced sub-setup" only allows to grab all the
rooted paths that have the same root node - i.e. all the paths in a forest
of paths. That is, the definition is less versatile since it does not allow
to grab all the rooted paths of an induced subtree. That is because these
rooted paths are no elements in the setup.

Note that an alternative definition of "induced sub-setup" could use the input
path to require that all additional paths from the setup must be prefixes to
that input path.

<!-- ======================================================================= -->
## subsetups A and D

Assuming a **partial setup** `S` and a set `(s in S)` ..

```
                             |-D(s)-partial--|
|-A(s)-total---------|       | |-> .. -> ..  |
| r(s) -> .. -> p(s) |-> s ->|-|->           |
|--------------------|       | |-> .. -> ..  |
                             |---------------|
                               c(s)     l(s)
```

* `A(s)` is a total sub-setup
* `D(s)` is (in general) a partial sub-setup

Note that `A(s)` is always **a total sub-setup**. Because of that, any non-root
set `(s in S)` always has a most significant `r(s) := max(A(s))` and a least
significant `p(s) := min(A(s))` **superset**.

Note that `D(s)` is in general **a partial sub-setup**. Because of that, there
is in general no least/most significant path in it. However, the subset of all
leaf paths `l(s)` can be described as the subset of all **minimal paths** in
`D(s)` and the subset of all child paths `c(s)` can be described as the subset
of all **maximal paths** in `D(s)`.

Note that each parent path in **a total setup** must have **one child path only**.
( That is because if a parent path had more than one child, then the setup would
have a pair of unrelated/incomparable paths. As such, the setup would not be
total ). Consequently, each parent path in a total setup always has a least
`l(p)` and a most significant path `c(p)`. Any non-empty total setup therefore
has **exactly one root and excatly one leaf path**.

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

Since each path in `A(s)` is a prefix to `s`, including `s` in `A` will still
restult in a total sub-setup `A*`. Likewise, since `s` is a prefix to each
path in `D`, including `s` in `D` will result in a sub-setup `D*` that is
either partial or total.

* `A*, A*(s) := (A(s)+{s}) := { a | (a ancestor-of s) or (a == s) }`
* `D*, D*(s) := (D(s)+{s}) := { d | (d descendant-of s) or (d == s) }`

Note that, since `s` is included as an element in `A*` and `D*`, both of these
sub-setups are **guaranteed to be non-empty**.

* `(#A* > 0)` and `(#D* > 0)` are both always true

Note that, `D*` is different to `D` isofar as `D` may in general have any
number of root paths (aka. maximal paths). In contrary to that, and since
`s` is a prefix to each path in `D`, sub-setup `D*` has a greatest
path and therefore **one and only one root path**.

* `(#RS(A*) == 1)`, `(#LS(D*) == 1)`
* `(#RS(D*) == 1)`, `(#LS(D*) >= 1)`

<!-- ======================================================================= -->
## paths of paths

```
|-A*-total-/-rp(s)--------|
| r(s) -> .. -> p(s) -> s |
|-------------------------|
```

Since each path in `A*` has a unique amount of elements, which is monotone
increasing from `r(s)` to `s`, the paths in `A*` can be used to define the
**rooted path** `rp(s)` of path `s` as an ordered sequence of paths, ordered
in decreasing order of signinficance.

* `rp, rp(s) := (s1..sN)` such that `(si in A*(s))`
* where `(rp[i] prefix-of rp[j])` for `(i < j)`
* where `(#rp[i]+1 == #rp[i+1])` for `(i in [1,#rp-1])`

Note that all rooted paths are **non-empty**. Furthermore, each rooted path
is **an ordered sequence** of paths. Also, the rooted path of each path in
a partial setup is **unique** to it.

Similar to that, **a path** can be formed from path `a` to path `b`
if and only if path `a` is an ancestor (aka. prefix) of path `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` := true if `p(a,b)` can be formed

<!-- ======================================================================= -->
## path-based definitions

Since paths can be formed in the context of a partial setup of paths,
path-based defintions such as the following can be introduced.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(s) := #rp(s)` - the level of path `s`
* `depth(s) := (#rp(s) - 1)` - the depth of path `s`
* `height(s) := max({ (#p-1) | p:=(s,..,l) for (l in LS) })`
* `(s peer-to t) := (#rp(s) == #rp(t))`

Note that each rooted path (e.g. `rp(s)`) in a setup of rooted paths `S` is
such that the number of paths in it (i.e. `#rp(s)`) is equal to the length of
its last path (i.e. `#s`). That is because `S` is required to contain every
prefix of `s`.

* `(#rp(s) == #s)` is true
* `(level(s) == #s)` is true
