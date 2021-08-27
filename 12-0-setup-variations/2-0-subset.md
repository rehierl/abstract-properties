
* (a < b), (a -> b) := (a subset-of b)
* (a < b), (down -> up) := "a" is down, "b" is up

<!-- ======================================================================= -->
# DI-RE-OV, partial

* the "DI xor RE xor OV" case
* everything that is possible in DI-RE and RE-OV

DI-RE summary

* no node tree (!)
* no parallel sub-components
* does not support all partial orders
* multiple roots, non-unique rooted paths
* upward-total, suffix-order

RE-OV summary

* a node tree - e.g. rps of a tree
* unclear if more than one component is possible ?
  e.g. not if rooted paths from a forest - disjoint
* parallel sub-components are possible
* seems to support all partial orders
* rooted paths are not necessarily unique
* possibly downward-total - e.g. rps of a tree
* possibly? - upward-total

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

* s1 subset-of s2 subset-of s3
* (#s1 < #s2 < #s3) - is true

remarks

* a node tree, **setup-t4-total**
* must have one root set only
* must have one leaf set only
