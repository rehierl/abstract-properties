
<!-- ======================================================================= -->
# superset, DI ex-or RE

- (si -> sj) := (si **superset-of** sj)
- if two sets are unrelated, then both must be **disjoint**
- assume each `si` to be a unique set of elements

```
possible
========
s1 -> s3
s2
```

- may have several disjoint root sets
- (s1,s3 disjoint-to s2) - must be true

```
possible
==========
s1 -|-> s2
    |-> s3
```

- a set may have any number of disjoint subsets
- each set may have multiple child sets

```
error (!)
==========
s1 -|-> s3
s2 -|
```

- s1 and s2 would both have to be supersets of s3
- s1 and s2 can not be disjoint error (!)
- a set can not have two disjoint supersets

<!-- ======================================================================= -->
## remarks

- downward-total, not upward-total
- a set can not have disjoint ancestors
- rooted paths are guaranteed to be unique
- a set may have disjoint descendants
- can not support all partial orders
