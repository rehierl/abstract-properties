
<!-- ======================================================================= -->
# the (default) level-order tree traversal

```
//- the default level-order tree traversal
traverseBFS(root) begin
  queue = new Queue()
  queue.enqueue(root)

  while (not queue.isEmpty) begin
    node = queue.dequeue()
    visit(node)

    for (child in node.childNodes) begin
      queue.enqueue(child)
    end
  end
end
```

Note that the level-order traversal trace begins with the tree's root, continues
with the root's child nodes, followed by the child nodes of its child nodes, and
so on. As such, the (default) level-order traversal trace contains the nodes in
tree order (i.e. ancestors before descendants) and also in child order (if one
exists). Because of that, the pre-order traversal trace is **order-preserving**.

```
n -|-> (ns .. ls)     =>     n -> (ns .. ls) -> (fc .. lc)
   |-> (fc .. lc)            n -> s -> c
```

Due to the above, **the level-order rule** requires to first embed a child order
(even if only temporary), and then to append the sequence of child nodes `c(n)`
to the sequence of subsequent siblings `s(n)`. Because of that, and unlike the
embedding of a child order, the pre-order rule does not build upon pre-existing
edges.

* the pre-order rule := `n -> (s × c)`

Note that, since a (P)arent appears before its subsequent (S)iblings and they
before the parent's (D)escendants, the level-order rule may also be referred
to as **the PSD rule/pattern** (aka. `p -> s -> d`).

Note that the level-order tree traversal is included as a dual counterpart to
the pre-order rule. However, even though it is order-preserving, it is not in
the focus of this discussion. That is because it does not keep a node and its
descendants in close proximity.

Note that, since the level-order rule does not keep a node and its descendants
in close proximity, **a particular order of execution is required** (see below).
