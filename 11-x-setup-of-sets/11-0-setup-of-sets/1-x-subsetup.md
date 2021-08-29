
<!-- ======================================================================= -->
# subsetup

Any subset of a setup can be described as **a sub-setup**.

Note that this is independent of the specific operator that
is seen as the basis of the related-to operator of a setup.

<!-- ======================================================================= -->
## induced sub-setup

Provided that the superset-of operator is seen as the basis of the related-to
operator, then **an induced sub-setup** `S[r]` is such that it contains the
specified set as a root set, and every subset in `S`:

* `S[r], S[r,*] := { s | (s subset-of r) or (s == r) }`

Note that both context-based definitions are such that the induced sub-setup
**grows (upwards) with the orientation** of the corresponding setup, not
against it.

<!-- ======================================================================= -->
## previous/old definitions

In case some old uses are still remaining ..

* `iT(s) := A*(s)` referred to as "induced total subsetup"
* `iP(s) := D*(s)` referred to as "induced partial subsetup"
* hint - similar to induced (partial) subtree
