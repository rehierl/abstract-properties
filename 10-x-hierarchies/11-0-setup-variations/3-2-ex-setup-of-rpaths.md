
- begin with a node tree, then ..
- form the set of all the rooted paths in it

<!-- ======================================================================= -->
# total / sequences

```
an ordered sequence and all the rooted paths in it
============================================================
s  := ( n1, n2, n3, n4, n5, n6 )
s6 := ( n1, n2, n3, n4, n5, n6 ) - the rooted path of a leaf
s5 := ( n1, n2, n3, n4, n5     )
s4 := ( n1, n2, n3, n4         )
s3 := ( n1, n2, n3             )
s2 := ( n1, n2                 )
s1 := ( n1                     ) - the rooted path of a root
```

subset-of
- (#s1 < .. < #s6) - the length of each sequence
- fits di-re, downward- and upward-total
- fits re-ov, downward- and upward-total

<!-- ======================================================================= -->
# the superset/RE-OV case

- ( note - a super-set is an ancestor to a sub-set )
- one root for the rooted path of each leaf - n1 is a root, s1 is a leaf (!)
- one leaf for the rooted path of each root - n6 is a leaf, s6 is a root (!)
- an upward-total poset

<!-- ======================================================================= -->
# the subset/RE-OV case

- ( note - a sub-set is an ancestor to a super-set )
- one root for the rooted path of each root - n1 is a root, s1 is a root
- one leaf for the rooted path of each leaf - n6 is a leaf, s6 is a leaf

<!-- ======================================================================= -->
# remarks

- **subset-of is consistent, superset-of is not**
- considering all the rooted paths in a tree
- shared prefixes, disjoint suffixes, overlap each other
- reversed scopes are related ex-or overlap each other
- the DI-RE case does not apply

well formed
- all the "prefixes" are included
- a prefix and all of its prefixes
- therefore - (#CE == 1)

no fitting counterpart to "prefix"
- unlike subset-/superset-of
- superstring-of - doesn't quite cover it
- superstring-of-prefix - better but clunky
- hence - somewhat inconsistent to superset-of
