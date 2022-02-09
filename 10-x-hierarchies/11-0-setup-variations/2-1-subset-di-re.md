
<!-- ======================================================================= -->
# subset, DI ex-or RE

- assume each si to be a unique set of elements
- (si -> sj) := (si subset-of sj)

```
possible
========
s1 -> s3
s2
```

- may have multiple disjoint root sets
- (s1,s3 disjoint-to s2) - must be true

```
possible
==========
s1 -|-> s3
s2 -|
```

- a set may have any number of disjoint subsets
- each set may have multiple parent sets

```
invalid (!)
===========
s1 -|-> s2
    |-> s3
```

- s2 and s3 would both have to be supersets to s1
- s2 and s3 would be related and not disjoint - error
- it is not possible for a set to have disjoint supersets
- supersets are by definition related - rooted paths
- each set has no more than one parent set

<!-- ======================================================================= -->
## remarks

- does not support parallel subcomponents
- does not support all partial orders

prefix/suffix order

- several rooted paths possible
- is upward total, a suffix order
- not downward total
