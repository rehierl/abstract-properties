
- begin with a node tree, then ..
- form the set of all the scopes in it

<!-- ======================================================================= -->
# total / sequences

```
an ordered sequence and all the scopes in it
======================================================
s  := ( n1, n2, n3, n4, n5, n6 )
s1 := { n1, n2, n3, n4, n5, n6 } - the scope of a root
s2 := {     n2, n3, n4, n5, n6 }
s3 := {         n3, n4, n5, n6 }
s4 := {             n4, n5, n6 }
s5 := {                 n5, n6 }
s6 := {                     n6 } - the scope of a leaf
```

superset-of
- (#s1 > .. > #s6) - the size of each set
- fits di-re, downward- and upward-total
- fits re-ov, downward- and upward-total

<!-- ======================================================================= -->
# the superset/DI-RE case

- ( note - a super-set is an ancestor to a sub-set )
- one root for the scope of each root - n1 is a root, s1 is a root
- one leaf for the scope of each leaf - n6 is a leaf, s6 is a leaf
- a downward total poset

<!-- ======================================================================= -->
# the subset/DI-RE case

- ( note - a sub-set is an ancestor to a super-set )
- one root for the scope of each leaf - n6 is a leaf, s6 is a root (!)
- one leaf for the scope of each root - n1 is a root, s1 is a leaf (!)
- an upward total poset

<!-- ======================================================================= -->
# remarks

- **superset-of is consistent, subset-of is not**
- considering all the scopes in a tree
- scopes are disjoint ex-or related
- the RE-OV case does not apply

well formed
- all the "suffixes" are included
- a suffix and all of its suffixes
- (#CE == 1) is true
