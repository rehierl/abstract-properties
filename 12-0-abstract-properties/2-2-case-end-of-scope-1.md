
<!-- ======================================================================= -->
## case - end of scope (eos-1)

```
(height)        (cursor)
l3 |          ====   | |
l2 |     ============|=|
l1 |=================|=| (width)
   | c1 - c2 - c3 - c4 |
   |  1    2    3    2 | (depth)
```

* what if p3 ended with c3
* and if c4 did not define p4

```
S := { s1, s2, s3 }
========================
s1 := { c1, c2, c3, c4 }
s2 := {     c2, c3, c4 }
s3 := {         c3     }
```

* `S` is a (total) set of sets
* one can define a total containment order
* the amount of subsets of scope `s2` is however insufficient
* `css(s2) = {c2,c4}` => `(#css(c2) > 1)`

conclusion

* considered invalid/incomplete
