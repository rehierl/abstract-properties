
<!-- ======================================================================= -->
## line-based visualizations

```
     |-s-----|       |-u-------------|      | a pre-order trace,
     |   |-t-|---|   |   |-v-----|   |      | including the scopes of
( n1,|n2,|n3,|n4,|n5,|n6,|n7, n8,|n9,|n10 ) | properties s, t, u, and v
     |===|===|   |   |   |=======|   |      |
         |=======|   |===============|      |
```

Since each node may be associated with more than one property, the scopes
of distinct properties may be disjoint (e.g. `s` and `u`), related (e.g.
`u` and `v`), or even overlap each other (e.g. `s` and `t`).

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 ) | - a pre-order trace
     =s======        =u==============       | - properties - s, u
         =t======        =v======           | - properties - t, v
```

Similar as before, the scopes of multiple properties can be visualized by
underlining the corresponding nodes (i.e. one continuous line per scope).
As such, the relationships between the scopes can be visually determined
with ease. In addition to that, and for the purpose of clarification,
property identifiers may be used as shown above.

Note that these line-based visualizations suggest a close relationship with
**Turing Machines**. That is, the pre-order trace of a tree can be understood
to define the input tape and each property an output tape of a Turing Machine.
To be more accurate, each cell in the input tape holds a reference to a node
and each cell in an output tape can be understood to hold a `false` value if
the node at the cell's position is not a node within the property's scope
- otherwise, such an output cell holds a `true` value.
