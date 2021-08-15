
<!-- ======================================================================= -->
## case - end of scope (eos-2)

```
(height)        (cursor)
l3 |          ==== ==|=|
l2 |     ============|=|
l1 |=================|=| (width)
   | c1 - c2 - c3 - c4 |
   |  1    2    3    3 | (depth)
```

* what if p3 ended with c3
* and if c4 did define p4

```
S := { s1, s2, s3, s4 }
========================
s1 := { c1, c2, c3, c4 }
s2 := {     c2, c3, c4 }
s3 := {         c3     }
s4 := {             c4 }
```

* `S` is a (partial) family of sets
* one can define a partial containment order
* `(#css(si) == 1)` for each `si`

```
s1 -> s2 -|-> s3
          |-> s4
```

conclusion

* each cell must define a new property
* for a tree of #N nodes, there must be #N scopes/properties

conclusion

* for each `si` such that `(#si > 1)`
* there must be `(#si-1)` subsets `sj`
* to ensure that `(css(si) == 1)`

conclusion

* distinct properties are defined by nodes
* that are adjacent and have the same depth
