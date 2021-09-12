
<!-- ======================================================================= -->
# border edges

Targeted to get a hold on those edges that connect sub-orders ...

<!-- ======================================================================= -->
## (Ex-1) an element-based removal from an ordered sequence

```
S                   \ R     = S*
========================================
( 1 -|-> 2 -|-> 3 ) \ ( 2 ) = ( 1 -> 3 )
     |----->|
```

In example Ex-1, the edges that are implicitly removed from `S` are neither
edges in `R` nor edges in `S*`. As such, these edges can be said to connect
suborder `S*` with suborder `R`. Based on that, there may in general be edges
which lead into a given suborder (e.g. `(1,2)`) and edges which lead out of
that suborder (e.g. `(2,3)`).

```
|-outer border of S*-----------------|
|      |-inner border of S*--|       |
|      ||-outer border of R-||       |
| 1 =|=||=>       2       ==||=|=> 3 |
|    | ||-------------------|| |     |
|    | |---------------------| |     |
|    |========================>|     |
|------------------------------------|
```

Based on that, and due to edge `(1,2)`, `S*` and `S` may both be said to be
a source to `R`. Likewise, and due to edge `(2,3)`, `S*` and `S` may both
also be said to be a sink to `R`.

In general, these kind of edges may be referred to as **border edges**. That
is because, by crossing the borders of the corresponding sub-orders, they
lead from one suborder to another. In contrary to that, edges which connect
an element of a suborder with another element in the same suborder, may be
described as **internal edges**. Similar to that, edges whose endpoints are
both not elements in a given suborder, may be described as **external edges**.

If further clarification is required, one might want to distinguish between
"incoming" (e.g. `(1,2)`) and "outgoing" border edges (e.g. `(2,3)`) in
regards to a known suborder.

<!-- ======================================================================= -->
## (Ex-2) a suffix-based removal from an un-ordered tree

```
S                 \ R            = S*
========================================
( 1 -> 2 -|-> 3 ) \ ( 2 -|-> 3 ) = ( 1 )
          |-> 4          |-> 4
```

In example Ex-2, a super-tree `S` has one border edge for each proper induced
subtree (e.g. `(1,2)` for `t[2]`). A proper induced subtree therefore has one
incoming border edge in its super-tree. Because of that, an induced subtree
can be seen as a sink, but not as a source to its super-tree.

```
|-S------------------|
||-S*-||-R----------||
|| 1 =||=> 2 =|=> 3 ||
||----||      |=> 4 ||
|      |------------||
|--------------------|
```

Note that including all the descendants of a node has the effect of getting rid
of all outgoing border edges. Based on that, one could describe a **suffix**
as a sub-order that has no outgoing border edge in its super-order. Likewise,
one could describe a **prefix** as a sub-order that has no incoming border edge
in its super-order. (Does that perspective support a generic description of
an infix/substring - e.g. only the min/max elements may have incoming/outgoing
border edges)?

Note that the incoming border edges can be said to represent the relationships
between the root nodes of both trees. As such, these edges can be said to
reflect the relationship between a super-tree and an induced sub-tree. These
incoming edges therefore reflect in general the relationships between subtrees.
(Recall that a tree is a sub-tree to itself - i.e. the only induced subtree
that has no incoming edge).

Note that, as a node tree, `S` is the cover graph (i.e. a transitive reduction)
of a partial order. That is, the underlying partial orders have in general more
than one incoming border edges for each "partial induced suborder".
