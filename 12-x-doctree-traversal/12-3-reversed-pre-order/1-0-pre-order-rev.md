
<!-- ======================================================================= -->
# the reversed pre-order tree traversal (preR)

```js
//- the default pre-order traversal
traverseInPreOrderR(node) {
  //- visit the node and enter its scope
  visit(node);

  //- recursively visit all child nodes
  //- in reversed child order
  for(child in node.childNodesRev) {
    traverseInPreOrderR(child)
  }

  //- exit the node's scope
}
```

Note that the reversed pre-order tree traversal is such that the document tree's
child order is reversed (i.e. a parent's first child will become its last child,
its second child its second to last child, and so on) before embedding it into
the node order of the unordered document tree.

Note that the reversed pre-order trace will contain the nodes in tree order
(i.e. ancestors before descendands), but not also in child order. Because of
that, the reversed pre-order trace is inconsistent with the child order and
therefore **not overall order-preserving**.

```
      subsequent           presequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (ls .. ns) -> n -|-> (ps .. fs)   |  n -|-> (ps .. fs)      |  n -|-> sR
                       |-> (lc .. fc)   |     |-> (lc .. fc)      |     |-> cR
                                        |                         |
                           child nodes  |                         |
```

Based on the above, the reversed pre-order traversal requires to first embed
the reversed child order, and then to append the reversed sequence of presequent
siblings `sR(n)` to the reversed sequence of child nodes `cR(n)`.

```
n -|-> (ps .. fs)     =>     -> n × (lc .. fc ..) × (ps .. fs ..)
   |-> (lc .. fc)            -> (n × cR × sR)
```

Recall that "reversed" denotes that the child order of a tree is turned upside
down. That is, each child order begins with the (former) last child and ends
with the (former) first child. Consequently, the node order of the ordered
doctree is such that `n` has its former next presequent sibling `ps` and its
former last child `lc` as its child nodes in the ordered doctree.

<!-- ======================================================================= -->
## order of execution

Since the reversed pre-order rule is such that a node and its descendants form
a substring to the trace of a tree, **no particular order of execution** is
required. That is because there is no significant change to the pre-order rule
itself since a node's next subsequent sibling `ps` will still be prefixed by
its former descendants in the unordered doctree.
