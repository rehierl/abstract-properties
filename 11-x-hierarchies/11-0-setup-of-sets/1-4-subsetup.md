
<!-- ======================================================================= -->
# subsetup

A subset of a setup can be described as **a sub-setup**.
Likewise, a superset of a setup can be described as **a super-setup**.

Note that this is independent of the specific operator that is used as the
basis of the setup's related-to operator.

<!-- ======================================================================= -->
## induced sub-setup

Provided that the superset-of operator is used as the basis of the related-to
operator, then **an induced sub-setup** `S[r]` is such that it contains the
specified set as a root set, and also every subset of `r` in `S`:

* `S[r], S[r,*] := { s | (s subset-of r) or (s == r) }`

Note that both context-based definitions (i.e. superset-of or subset-of)
are such that the induced sub-setup **grows with the orientation** of the
corresponding operator, not against it.
