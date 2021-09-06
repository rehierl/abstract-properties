
<!-- ======================================================================= -->
# the default pre-order tree traversal (D)

```
//- the default pre-order traversal
traverseInPreOrderD(node) begin
  visit(node)
  for(child in node.childNodes) begin
    traverseInPreOrderD(child)
  end
end
```

Note that the pre-order trace will contain the nodes in tree order (i.e.
ancestors before descendants) and also in child order (if one does exist).
Because of that, the pre-order trace is **order-preserving**.

```
      presequent           subsequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> (ns .. ls)      |  n -|-> s
                       |-> (fc .. lc)   |     |-> (fc .. lc)      |     |-> c
                                        |                         |
                           child nodes  |                         |
```

Based on the above algorithm, the pre-order traversal requires to first embed
a child order (even if only temporary), and then to append the sequence of
subsequent siblings `s(n)` to the sequence of child nodes `c(n)`.

```
n -|-> (ns .. ls)     =>     -> n × (fc .. lc ..) × (ns .. ls ..)
   |-> (fc .. lc)            -> (n × c × s)
```

* the (default) pre-order rule := `(n × c × s)`

Note that this pre-order rule can be understood such that it defines a sequence
of nodes which replaces the node and all the nodes subsequent to it. Based on
that it can be said to define how to restructure the tree in regards to the
current node `n`.

<!-- ======================================================================= -->
## order of execution

Since the pre-order rule is such that a node and descendants form a substring
to the trace of a tree, **no particular order of execution** is required.

That is, even though the root of a tree will in general be used as a starting
point, one can apply the pre-order rule in any order and still end up with
the exact same trace of nodes.

(Think in terms of linked lists, not in terms of actual sequences/arrays).

<!-- ======================================================================= -->
## the (preD <=> postR) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace such that both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`

Note that, due to this correspondence, the reversed post-order trace
is **order-reversing**.
