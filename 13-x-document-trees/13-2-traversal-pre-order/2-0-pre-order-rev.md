
<!-- ======================================================================= -->
# the reversed pre-order tree traversal (R)

```
//- the default pre-order traversal
traverseInPreOrderR(node) begin
  visit(node)
  for(child in node.childNodesRev) begin
    traverseInPreOrderR(child)
  end
end
```

Note that the reversed pre-order trace will contain the nodes in tree order
(i.e. ancestors before descendands), but not in child order. Because of that,
the reversed pre-order trace is inconsistent with the child order and therefore
overall **not order-preserving**.

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

* the reversed pre-order rule := `(n × cR × sR)`

Recall that "reversed" denotes that the child order of a tree is turned upside
down. That is, each child order begins with the (former) last child and ends
with the (former) first child. Consequently, the node order of the ordered
doctree is such that `n` has its former next presequent sibling `ps` and its
former last child `lc` as its child nodes in the ordered doctree.

<!-- ======================================================================= -->
## order of execution

Since the reversed pre-order rule is such that a node and its descendants
form a substring to the trace of a tree, **no particular order of execution**
is required. That is because there is no significant change to the pre-order
rule itself since a node's next subsequent sibling `ps` will still be prefixed
by its former descendants in the unordered doctree.

<!-- ======================================================================= -->
## the (preR <=> postD) correspondence

Note that the reversed pre-order trace corresponds with the default post-order
trace such that both traces are reversed to each other.

* `preR(n) := n × (lc .. fc ..)`
* `postD(n) := (.. fc .. lc) × n `
* `preR(T)` is reversed to `postD(T)`
