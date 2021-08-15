
<!-- ======================================================================= -->
# shared (abstract) properties

As was introduced with abstract properties, **each line** drawn above/below
an ordered sequence can be said to correspond with a subset over that sequence,
And since any such sequence can be said to isomorphic to a total order, each
such line can be described as **an interval**. Based on that, each layer in
the side scroller can be said to visualize **an induced (total) suborder**.

```
(height)
l3 |           =====|
l2 |      ==========|
l1 |================| (width)
   | c1 - c2 - c3 ->|
```

Furthermore, each first element in an interval can be described as the defining
node/element of an abstract property. That is, `ci` is the defining node of
`pi`, and layer/line `li` the visual representation of its scope `s(ci)`.

* `s(pi) := [ni,*]`
* `s(p1) = {c1, c2, c3}`, `s(p2) = {c2, c3}` and `s(p3) = {c3}`

Since each next cell `cj` is, at this point, understood to define a new property
`pj`, each next cell can be said to be within the scope of all those properties
that were declared by all the `ci` that are presequent to `cj`.

Since a property `pi` has a scope `s(pi)` that may extend over any number of
cells, one can state that **properties are shared across cells**.

* cells within the scope of a property
* properties are shared across cells

Since any cell may be an element in any number of scopes, any cell an be said
to be associated with each such property. That is, one can assume that each
cell is associated with a set of properties `p(ci)` which contains all of
those properties to which the cell belongs.

* `p(ci) := { pj | (ci in s(pj)) }`
* `p(c1) = {p1}`, `p(c2) = {p1, p2}` and `p(c3) = {p1, p2, p3}`

Since a cell `ci` has a set of properties `p(ci)` that may extend over any
number of properties, one can state that **cells are shared across properties**.

* properties may apply to multiple cells
* cells are shared across properties

In essence this describes **an n:m relationship** between cells and properties.
That is, each property can be associated with any number of cells, and any cell
can be associated with any number of properties.

Due to the above, relationships can be defined based on the relationships
between the sets of cells `s(pi)` and the sets of properties `p(ci)`.
