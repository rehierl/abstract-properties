
<!-- ======================================================================= -->
# subsetup

Any subset of a setup can be described as **a sub-setup**.

Note that this is independent of the specific operator that
is seen as the basis of the related-to operator of a given setup.

<!-- ======================================================================= -->
## induced sub-setup

Provided that the superset-of operator is seen as the basis of the related-to
operator, then **an induced sub-setup** `S[r]` is such that it contains the
specified set as a root set, and every subset in `S`:

* `S[r] := { s | (s == r) or (s subset-of r) }`

If, in contrary to that, the subset-of operator is seen as the basis of the
related-to operator, then `S[r]` is such that it contains the specified root
set `r` and every superset in `S`:

* `S[r] := { s | (s == r) or (s superset-of r) }`

Note that both context-based definitions are such that the induced sub-setup
**grows with the orientation** of the corresponding setup, not against it.

<!-- ======================================================================= -->
## previous/old definitions

In case some old uses are still remaining ..

* `iT(s) := A*(s)` referred to as "induced total subsetup"
* `iP(s) := D*(s)` referred to as "induced partial subsetup"
* similar - induced (partial) subtree
