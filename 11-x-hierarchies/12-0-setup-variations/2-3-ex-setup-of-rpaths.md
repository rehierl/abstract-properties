
- prefixes derived from the rooted paths of a single tree
- subset-of is consistent, superset-of is not

<!-- ======================================================================= -->
# total pov / sequences

```
s1 := ( n1, n2, n3, n4, n5, n6 ) - the rp of a leaf
s2 := ( n1, n2, n3, n4, n5     )
s3 := ( n1, n2, n3, n4         )
s4 := ( n1, n2, n3             )
s5 := ( n1, n2                 )
s6 := ( n1                     ) - the rp of the root
```

subset-of <=> prefix-of
- (#s6 < .. < #s1)
- fits di-re, downward- and upward-total
- fits re-ov, downward- and upward-total

<!-- ======================================================================= -->
# the superset/RE-OV case

- a root for each rp of a leaf
- one leaf for the rp of the root
- an upward-total poset

<!-- ======================================================================= -->
# the subset/RE-OV case

- one root for the rp of the root
- a leaf for the rp of each leaf
- a downward-total poset

remark
- a rooted path has related prefixes only

<!-- ======================================================================= -->
# remarks

which cases
- assuming all rooted paths from an entire tree
- shared prefixes, disjoint suffixes, overlap each other
- the DI-RE cases can not apply

well formed
- all "prefixes" are included
- therefore - (#CE == 1)

no fitting antonymous to prefix-of
- unlike subset-/superset-of
- superstring-of - doesn't quite cover it
- superstring-of-prefix - better but clunky
- hence - inconsistent to superset-of
