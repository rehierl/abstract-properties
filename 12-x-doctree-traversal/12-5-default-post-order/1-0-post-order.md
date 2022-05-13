
<!-- ======================================================================= -->
# the default post-order tree traversal (postD)

```js
//- the default post-order traversal
traverseInPostOrder(node) begin
  //- enter the node's scope

  //- recursively visit all child nodes
  for(child in node.childNodesFTL) begin
    traverseInPostOrder(child)
  end

  //- visit the node and exit its scope
  visit(node)
end
```

Note that the default post-order trace will contain a node after all of its
descendants (i.e. ancestors subsequent to descendants - not presequent).
Because of that, the post-order trace is inconsistent with the tree order
and therefore **not order-preserving**.

```
      subsequent           presequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (ls .. ns) -> n -|-> (ps .. fs)   |  n -|-> (ps .. fs)      |  n -|-> sR
                       |-> (lc .. fc)   |     |-> (lc .. fc)      |     |-> cR
                                        |                         |
                           child nodes  |                         |
```

Based on the above algorithm, the post-order traversal requires to prepend a
node `n` and its subsequent siblings `s(n)` by its child order `c(n)`.

```
n -|-> (ns .. ls)     =>     -> (.. fc .. lc) × n × (.. ns .. ls)
   |-> (fc .. lc)            -> (c × n × s)
```

<!-- ======================================================================= -->
## order of execution

Since the post-order rule is such that a node and its descendants form a
substring to the trace of a tree, **no particular order of execution**
is required.
