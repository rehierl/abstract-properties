
* (a < b), (a -> b) := (a superset-of b)
* (a < b), (down -> up) := "a" is down, "b" is up

<!-- ======================================================================= -->
# DI-RE-OV, partial

* the "DI xor RE xor OV" case
* everything that is possible in DI-RE and RE-OV

DI-RE summary

* a node tree, **setup-t1-partial**
* no parallel sub-components
* does not support all partial orders
* unique rooted paths
* downward-total, prefix-order

RE-OV summary

* unclear if more than one component is possible ?
  e.g. not if rooted paths from a forest - disjoint
* parallel sub-components are possible
* seems to support all partial orders
* rooted paths are not necessarily unique
* possibly upward-total - e.g. rps of a tree
* possibly? - downward-total

remarks

* application - the rooted paths of a tree
* DI-RE-OV - to support the rps of a forest

<!-- ======================================================================= -->
# RE-only, total

```
possible
==============
s1 -> s2 -> s3
```

* s1 superset-of s2 superset-of s3
* (#s1 > #s2 > #s2) - is true

remarks

* a node tree, **setup-t2-total**
* must have one root set only
* must have one leaf set only