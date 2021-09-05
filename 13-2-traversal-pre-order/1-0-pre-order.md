
<!-- ======================================================================= -->
# the pre-order tree traversal

```
//- the default pre-order tree traversal
traverseInPreOrder(node) begin
  visit(node)
  for(child in node.childNodes) begin
    traverseInPreOrder(child)
  end
end
```

Note that the pre-order trace will contain the nodes in tree order (i.e.
ancestors before descendants) and also in child order (if it exists).
Because of that, the pre-order trace is **order-preserving**.

```
n -|-> (ns .. ls)     =>     n -> (fc .. lc) -> (ns .. ls)
   |-> (fc .. lc)            n -> c -> s
```

Due to the above, **the pre-order rule** requires to first embed a child order
(even if only temporary), and then to append the sequence of subsequent siblings
`s(n)` to the sequence of child nodes `c(n)`. Because of that, and unlike the
embedding of a child order, the pre-order rule does not build upon pre-existing
edges.

* the pre-order rule := `n -> (c × s)`

Note that, since a (P)arent appears before its (D)escendants, and they before
any of its subsequent (S)iblings, the pre-order rule may also be referred to
as **the PDS rule/pattern** (aka. `p -> d -> s`).

Note that **no particular order of execution** is required (see below).

<!-- ======================================================================= -->
## order of execution

Since the pre-order rule is such that it is required to apply to each parent
in a tree (i.e. a generic rule), and since a node and all of its descendants
form a substring to the trace of a tree, **no particular order of execution**
is required.

That is, even though the root of a tree will in general be used as a starting
point, one can apply the pre-order rule in any order and still end up with
the exact same trace of nodes.

(Think in terms of linked lists, not in terms of actual sequences/arrays).
