
<!-- ======================================================================= -->
# remarks

The following contains further definitions, which are analogous to those that
were defined for setup of sets.

<!-- ======================================================================= -->
## (induced) subsetup

A subset of a setup of trees can be described as **a sub-setup** of trees.
Likewise, a superset of a setup can be described as **a super-setup**.

Assuming the supertree-of operator as the basis of the related-to operator,
then **an induced subsetup** `S[r]` is such that it contains the specified
tree `r` as its root tree, and also every subtree of `r` in `S`:

* `S[r], S[r,*] := { t | (t subtree-of r) or (t == r) }`

<!-- ======================================================================= -->
## subsetups A() and D()

Note that, if one focusses on "a known fixed rule", then `A(s)` can be said
to define an induced total sub-setup. Likewise, `D(s)` can be said to define
an induced partial sub-setup.

In a partial setup and total setups, `A(s)` is a total subsetup. Because of
that, any non-root tree always has a most significant and a least significant
supertree in `A(s)`. In contrary to that, the setup must be a total setup for
`D(s)` to be a total subsetup since each parent tree may have any number of
child trees. Because of that, a partial setup always is
**downward-total, but not necessarily also upward-total**.

As with setups of sets, `A(t)` and `D(t)` can both be extended to include the
input tree `t` as the leaf in `A*(t)` and as the root in `D*(t)`. This ensures
that both results will always be non-empty.

* `A*(t) := A(t) + {t}`, `D*(t) := D(t) + {t}`

<!-- ======================================================================= -->
## paths of trees

Since each tree in `A*` has a unique amount of nodes, the sets trees in `A*`
can be used to define the **rooted path** `rp(t)` of tree `t` as an ordered
sequence of trees, ordered in decreasing order of significance.

Based on that, **a path** can be formed from tree `a` to tree `b`,
if and only if tree `a` is an ancestor of tree `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` := true if `p(a,b)` can be formed

Since paths can be formed in the context of a partial setup of trees,
path-based defintions, such as the following, can be introduced.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(t) := #rp(t)` - the level of tree `t`
* `depth(t) := (#rp(t) - 1)` - the depth of tree `t`
* `height(t) := max({ (#p-1) | p:=(t,..,l) for (l in LS) })`
* note - in regards to the overall setup `S`
