
<!-- ======================================================================= -->
# subset, RE ex-or OV

- (si -> sj) := (si **subset-of** sj)
- if two sets are unrelated, then both must **overlap**
- assume each `si` to be a unique set of elements

```
possible
========
s1 -> s3
s2
```

- (s1 subset-of s3) - must be true
- (s2 overlaps s1,s3) - must be true

```
possible
==========
s1 -|-> s2
    |-> s3
```

- (s2 overlaps s3) - must be true
- (s1 subset-of s2,s3) - must be true
- (s1 subset-of (s2 + s3) - must be true
- a set may have overlapping supersets

```
possible
==========
s1 -|-> s3
s2 -|
```

- (s1 overlaps s2) - must be true
- (s1,s2 subset-of s3) - must be true
- ((s1 + s2) subset-of s3) - must be true
- a set may have overlapping subsets

```
possible
==================
s1 -|-> s2 -|-> s4
    |-> s3 -|
```

- (s2 overlaps s3) - must be true
- (s1 subset-of s2,s3) - must be true
- ((s2 + s3) subset-of s4) - must be true
- parallel sub-components are possible
- note - monotone increasing counts of elements

<!-- ======================================================================= -->
## remarks

- not downward-total, not upward-total
- a set may have overlapping ancestors
- a set may have multiple rooted paths
- a set may have overlapping descendants
- parallel sub-components are possible
- seems to support all partial orders
