
<!-- ======================================================================= -->
# superset, DI ex-or RE

- assume each `si` to be a unique set of elements
- (si -> sj) := (si superset-of sj)

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
invalid (!)
===========
s1 -|-> s3
s2 -|
```

- s1 and s2 would both have to be supersets of s3
- s1 and s2 would have to be related and not disjoint - error
- it is not possible for a set to have disjoint supersets
- supersets are by definition related -> rooted paths
- each set has no more than one parent set

<!-- ======================================================================= -->
## remarks

- does not support parallel subcomponents
- does not support all partial orders

prefix/suffix order

- unique rooted paths
- is downward total, a prefix-order, unique rooted paths
- not upward total
