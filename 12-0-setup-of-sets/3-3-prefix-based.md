
- the prefix-based approach
- a set of substrings/prefixes

<!-- ======================================================================= -->
# total pov / sequences

```
s1 := ( n1, n2, n3, n4, n5, n6 )
s2 := ( n1, n2, n3, n4, n5     )
s3 := ( n1, n2, n3, n4         )
s4 := ( n1, n2, n3             )
s5 := ( n1, n2                 )
s6 := ( n1                     )
```

superset-of <=> superstring-of
- (#s1 > .. > #s6)
- fits di-re, downward/upward total, insofar a prefix/suffix order
- fits re-ov, downward/upward total, insofar a prefix/suffix order

subset-of <=> prefix-of
- (#s6 < .. < #s1)
- fits di-re, downward/upward total, insofar a prefix/suffix order
- fits re-ov, downward/upward total, insofar a prefix/suffix order

<!-- ======================================================================= -->
# generalized pov

<!-- ======================================================================= -->
# remarks

no fitting antonymous to prefix-of
- superstring-of - doesn't quite cover it
- superstring-of-prefix - better but clunky
- unlike subset-/superset-of
