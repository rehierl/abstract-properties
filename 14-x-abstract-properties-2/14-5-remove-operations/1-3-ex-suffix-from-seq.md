
<!-- ======================================================================= -->
# example - remove a suffix from a sequence

As mentioned before, there are two base orders in the context of an ordered
sequence: (1) the trivial suborder, and (2) the overall total order which
is defined by the index order of the ordered sequence. Because of that, the
suffix based removal is also available as a base order:

```
S               \ R          = S*
====================================
( 1 -> 2 -> 3 ) \ ( 2 -> 3 ) = ( 1 )
```

Given a sequence `S` and a to-be-removed element (e.g. `2`), we can treat the
element as the root of an induced subtree (e.g. `S[2,*]`). That is, the input
node can be understood to define a suffix of `S`.

* `S* := (S \ R)` where `R := S[2,*]`
