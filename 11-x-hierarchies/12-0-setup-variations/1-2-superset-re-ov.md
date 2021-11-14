
<!-- ======================================================================= -->
# superset, RE xor OV

```
components ?
========
s1 -> s3
      s2
```

* (#s1 > #s3) - must be true
* (s1 superset-of s3) - must be true
* (s2 overlaps s1,s3) - must be true

```
possible
==========
s1 -|-> s3
s2 -|
```

* (s1 overlaps s2) - must be true
* (s1,s2 superset-of s3) - must be true
* (s3 subset-of (s1 & s2)) - must be true
* a set may have overlapping supersets

```
possible
==========
s1 -|-> s2
    |-> s3
```

* (s2 overlaps s3) - must be true
* (s1 superset-of s2,s3) - must be true
* (s1 superset-of (s2 + s3)) - must be true
* a set may have overlapping subsets

```
possible
====================
s1 -|-> s2 -|-> s4
    |-> s3 -|
```

* (s2 overlaps s3) - must be true
* (s1 superset-of (s2 + s3)) - must be true
* ((s2 & s3) superset-of s4) - must be true
* note - monotone decreasing counts of elements

<!-- ======================================================================= -->
## remarks

* seems to support all partial orders
* parallel sub-components are possible
* rooted paths are not necessarily unique
