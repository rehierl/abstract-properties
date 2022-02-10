
<!-- ======================================================================= -->
# subset, DI ex-or RE

- (si -> sj) := (si **subset-of** sj)
- if two sets are unrelated, then both must be **disjoint**
- assume each `si` to be a unique set of elements

```
possible
========
s1 -> s3
s2
```

- may have multiple disjoint root sets
- (s1,s3 disjoint-to s2) - must be true

```
error (!)
==========
s1 -|-> s2
    |-> s3
```

- s2 and s3 would both have to be supersets to s1
- s2 and s3 can not be disojint - errror (!)
- a set can not have two disjoint supersets

```
possible
==========
s1 -|-> s3
s2 -|
```

- a set may have any number of disjoint subsets
- each set may have multiple parent sets

<!-- ======================================================================= -->
## remarks

- upward-total, not downward-total
- a set can have disjoint ancestors
- multiple rooted paths are possible
- a set can not have disjoint descendants
- can not support all partial orders
