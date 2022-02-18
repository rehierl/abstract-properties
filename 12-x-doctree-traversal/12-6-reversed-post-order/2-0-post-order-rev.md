
<!-- ======================================================================= -->
# the reversed post-order tree traversal (R)

```js
//- the reversed post-order traversal
traverseInPostOrderRev(node) {
  for(child in node.childNodesRev) {
    traverseInPostOrderRev(child);
  }
  visit(node);
}
```

Note that the reversed post-order trace will contain a node after all of its
descendants (i.e. ancestors subsequent to descendants - not presequent).
Because of that, the reversed post-order trace is inconsistent with the tree
order and therefore **not order-preserving**.

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
node and all the nodes subsequent to it with its reversed child order `cR(n)`,
followed by the node `n`, followed by its reversed sequence of presequent
siblings `sR(n)`.

```
n -|-> (ps .. fs)     =>     -> (.. lc .. fc) × n × (.. ps .. fs)
   |-> (lc .. fc)            -> (cR × n × sR)
```

* the reversed post-order rule := `(cR × n × sR)`

<!-- ======================================================================= -->
## order of execution

Since the reversed post-order rule is such that a node and its descendants
form a substring to the trace of a tree, **no particular order of execution**
is required.

<!-- ======================================================================= -->
## the (postR <=> preD) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace such that both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`

Note that, due to this correspondence, the reversed post-order trace
is **order-reversing**.
