
<!-- ======================================================================= -->
# remarks

The following contains further definitions, which are analogous to those that
were defined for setups of sets.

<!-- ======================================================================= -->
## (induced) subsetup

The subset of a setup may be described as **a sub-setup**.

* `(A subsetup-of B) := (A subset-of B)`

Assuming the supertree-of operator as the basis of the related-to operator,
**an induced subsetup** `S[r]` is such that it contains tree `r` as its root,
and also all the subtrees of `r` in `S`:

* `S[r], S[r,*] := { t | (t subtree-of r) or (t == r) }`

<!-- ======================================================================= -->
## subsetups A() and D()

In partial and total setups, `A(t)` is a total subsetup. Because of that, any
non-root tree always has a most significant and a least significant supertree
in `A(t)`. In contrary to that, a setup must be total for `D(t)` to be a total
since each parent may have any number of child trees. Because of that, a partial
setup is always downward-, but not necessarily also upward-total.

As with setups of sets, `A(t)` and `D(t)` can both be extended to include the
input tree `t` as the leaf in `A*(t)` and as the root in `D*(t)`. This ensures
that both subsetups are always non-empty.

* `A*(t) := A(t) + {t}` and `D*(t) := D(t) + {t}`

Note that, if one focusses on the aspect of "a known fixed rule", then `A(s)`
can be said to define an induced total sub-setup. Likewise, `D(s)` can be said
to define an induced partial sub-setup.

<!-- ======================================================================= -->
## paths of trees

Since each tree in `A*(t)` has a unique amount of nodes, the trees in it allow
to define the **rooted path** `rp(t)` of tree `t` as an ordered sequence of
trees, ordered in decreasing order of significance.

Based on that, **a path** can be formed from tree `a` to tree `b`,
if tree `a` is an ancestor of `b`.

* `p(a,b) := {a} × (rp(b) \ rp(a))` iff `(a ancestor-of b)`
* `(rp(a) prefix-of rp(b))` is true - i.e. the removal of a prefix
* `aPb` is true if `p(a,b)` can be formed

Since paths can be formed in the context of a partial setup of trees, all other
path-based defintions can be assumed to be available.

* `(a connected-to b)` := true if `aPb` or `bPa`
* `level(t) := #rp(t)` - the level of tree `t`
