
<!-- ======================================================================= -->
# Visualizing scopes

As shown below, the scope of an abstract property can be visualized by
underlining all of the nodes in its scope.

```
a - b - c - d - e ->
       ============= p
```

Note that it is difficult to underline no node at all. Consequently, it is
helpful to count a defining node towards the scopes of the properties it
declares.

Assuming that node `c` is understood to define property `p` (i.e. its defining
node `d(p)`), then the scope `s(p)` of `p` can be understood to contain all of
the nodes within the open interval `[c,*]` over the corresponding node order.

* `d(p) = c`
* `s(p) = [d(p),*] = { c, d, ... }`

```
       |-p-------------|
a - b -|- c - d - e -> |
       |===============|
```

If need be, one can extend the line that is used to highlight the nodes within
a scope, by simply drawing a box that has the line as one of its edges. Based
on that, it is visually unambiguous which nodes are included, and which ones
are not. That is, one can visually determine the (ordered) set of nodes the
scope contains.
