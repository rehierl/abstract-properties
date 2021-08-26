
* (a < b), (a -> b) := (a subset-of b)
* (a < b), (down -> up) := "a" is down, "b" is up

<!-- ======================================================================= -->
# DI-RE-OV, partial

* the "DI xor RE xor OV" case
* everything that is possible in DI-RE and RE-OV

DI-RE summary

* no node tree
* no parallel sub-components
* does not support all partial orders
* multiple roots, non-unique rooted paths
* upward-total, suffix-order

RE-OV summary

* unclear if more than one root is possible (?)
* parallel sub-components are possible
* seems to support all partial orders
* rooted paths are not necessarily unique
* TODO - applications ?!?
* possibly? - downward-total, prefix-order
* possibly? - upward-total, suffix-order

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

* a node tree
* must have one root set only
* must have one leaf set only
