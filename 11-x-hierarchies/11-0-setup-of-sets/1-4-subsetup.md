
<!-- ======================================================================= -->
# subsetup

A subset of a setup can be described as **a sub-setup**. Likewise, a superset
of a setup can be described as **a super-setup**.

Note that this is independent of the specific operator that is used as the
basis of the setup's related-to operator. However, the requirements of the
source setup must be understood to carry over to the corresponding sub-setup
or super-setup.

Provided that the superset-of operator is used as the basis of the related-to
operator, then **an induced sub-setup** `S[r]` is such that it contains set
`r` as a root, and also any subset of `r`.

* `S[r], S[r,*] := { s | (s subset-of r) or (s == r) }`

Note that an induced sub-setup corresponds with an interval over the setup
while adhereing to the setup's definitions.

Note that both context-based definitions (i.e. superset-of or subset-of) are
such that the induced sub-setup **grows with the orientation** of the
corresponding operator, not against it.
