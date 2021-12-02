
- scopes derived from a single tree
- superset-of is consistent, subset-of is not

<!-- ======================================================================= -->
# total / sequences

```
an ordered sequence and all the scopes of its nodes
========================================================
s  :=   n1, n2, n3, n4, n5, n6
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

- s1 as the only root
- a leaf for each 1-element subset
- a downward total poset

<!-- ======================================================================= -->
# the subset/DI-RE case

- s1 as the only leaf
- a root for each 1-element subset
- an upward total poset

<!-- ======================================================================= -->
# remarks

which cases
- assuming all the scopes in a tree
- scopes are disjoint ex-or related
- the RE-OV case can not apply

well formed
- all the "suffixes" are included
- (#CE == 1) is true

ordered sequences
- an ordered sequence corresponds with a set
- sub-/super-sequence/string map to sub-/super-set
