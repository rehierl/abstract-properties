
- scopes derived from a single tree
- superset-of is consistent, subset-of is not

<!-- ======================================================================= -->
# total pov / sequences

```
s1 := { n1, n2, n3, n4, n5, n6 } - the scope of the root
s2 := {     n2, n3, n4, n5, n6 }
s3 := {         n3, n4, n5, n6 }
s4 := {             n4, n5, n6 }
s5 := {                 n5, n6 }
s6 := {                     n6 } - the scope of a leaf
```

superset-of
- (#s1 > .. > #s6)
- fits di-re, downward- and upward-total
- fits re-ov, downward- and upward-total

<!-- ======================================================================= -->
# the superset/DI-RE case

- s1 as a root
- a leaf for each 1-element subset
- a downward total poset

<!-- ======================================================================= -->
# the subset/DI-RE case

- a root for each 1-element subset
- s1 as the only leaf
- an upward total poset

<!-- ======================================================================= -->
# remarks

which cases
- assuming all scopes from an entire tree
- scopes are disjoint xor related
- the RE-OV cases can not apply

well formed
- all "suffixes" are included
- therefore - (#CE == 1)

ordered sequences
- recall that an ordered sequence corresponds with a set
- sub-/super-sequence maps to sub-/super-set
- sub-/super-string maps to sub/-/super-set
