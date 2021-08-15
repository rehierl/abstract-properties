
<!-- ======================================================================= -->
## case - no new property

```
(height)        (cursor)
l3 |          =======|=|
l2 |     ============|=|
l1 |=================|=| (width)
   | c1 - c2 - c3 - c4 |
   |  1    2    3    3 | (depth)
```

* what if c4 did not define p4?

```
S := { s1, s2, s3 }
========================
s1 := { c1, c2, c3, c4 }
s2 := {     c3, c3, c4 }
s3 := {         c3, c4 }
```

* `S` is a (total) set of sets
* one can define a total containment order
* the amount of subsets of scope `s3` is however insufficient
* `css(s3) = {c3,c4}` => `(#css(s3) > 1)`

remark

* by replacing the subsets `{c3,c4}` with `{c5}`
* i.e. remove `c3` and `c4`, then add `c5`
* one can still derive a (total) family of scopes
* corresponds with "a merger of cells"

conclusion

* considered invalid/incomplete
