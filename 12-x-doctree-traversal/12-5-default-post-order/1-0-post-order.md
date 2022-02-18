
<!-- ======================================================================= -->
# the default post-order tree traversal (D)

```js
//- the default post-order traversal
traverseInPostOrder(node) begin
  for(child in node.childNodes) begin
    traverseInPostOrder(child)
  end
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

Based on the above algorithm, the post-order traversal requires to replace a
node and all the nodes subsequent to it with its child order `c(n)`, followed
by the node `n`, followed by its sequence of subsequent siblings `s(n)`.

```
n -|-> (ns .. ls)     =>     -> (.. fc .. lc) × n × (.. ns .. ls)
   |-> (fc .. lc)            -> (c × n × s)
```

* the (default) post-order rule := `(c × n × s)`

<!-- ======================================================================= -->
## order of execution

Since the post-order rule is such that a node and its descendants form a
substring to the trace of a tree, **no particular order of execution**
is required.

<!-- ======================================================================= -->
## the (preR <=> postD) correspondence

Note that the reversed pre-order trace does correspond wqith the default
post-order trace such that both traces are reversed to each other.

* `preR(n) := n × (lc .. fc ..)`
* `postD(n) := (.. fc .. lc) × n `
* `preR(T)` is reversed to `postD(T)`
