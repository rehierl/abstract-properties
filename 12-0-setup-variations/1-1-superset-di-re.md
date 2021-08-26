
<!-- ======================================================================= -->
# superset, DI xor RE

```
possible
========
s1 -> s3
s2
```

* may have multiple disjoint root sets
* (s1,s3 disjoint-to s2) - must be true

```
possible
==========
s1 -|-> s2
    |-> s3
```

* a set may have any number of disjoint subsets
* each set may have multiple child sets

```
! invalid !
===========
s1 -|-> s3
s2 -|
```

* s1 and s2 would both have to be supersets to s3
* s1 and s2 would be related and not disjoint - error
* it is not possible for a set to have disjoint supersets
* supersets are by definition related - rooted paths
* each set has no more than one parent set

<!-- ======================================================================= -->
## remarks

* does not support parallel subcomponents
* does not support any partial order

prefix/suffix order

* unique rooted paths
* is downward total -> a prefix order
* not upward total -> no suffix order
