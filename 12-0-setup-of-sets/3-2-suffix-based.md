
- the suffix-based approach
- a set of substrings/suffixes

<!-- ======================================================================= -->
# total pov / sequences

```
s1 := ( n1, n2, n3, n4, n5, n6 )
s2 := (     n2, n3, n4, n5, n6 )
s3 := (         n3, n4, n5, n6 )
s4 := (             n4, n5, n6 )
s5 := (                 n5, n6 )
s6 := (                     n6 )
```

superset-of <=> superstring-of
- (#s1 > .. > #s6)
- fits di-re, downward/upward total, insofar a prefix/suffix order
- fits re-ov, downward/upward total, insofar a prefix/suffix order

subset-of <=> suffix-of
- (#s6 < .. < #s1)
- fits di-re, downward/upward total, insofar a prefix/suffix order
- fits re-ov, downward/upward total, insofar a prefix/suffix order

<!-- ======================================================================= -->
# generalized pov

<!-- ======================================================================= -->
# remarks

no fitting antonymous to suffix-of
- superstring-of - doesn't quite cover it
- superstring-of-suffix - better but clunky
- unlike subset-/superset-of
