
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
that it can be said to define how to restructure the tree in regards to some
current node `n`.

<!-- ======================================================================= -->
## order of execution

Since the pre-order rule is such that a node and descendants form a substring
to the trace of a tree, **no particular order of execution** is required.

That is, even though the root of a tree will in general be used as a starting
point, one can apply the pre-order rule in any order and still end up with the
exact same trace of nodes.

(Think in terms of linked lists, not in terms of actual sequences/arrays).

<!-- ======================================================================= -->
## (set of) pre-order edges (?)

The pre-order rule allows to pre-calculate a set of edges. However, as can
be seen below, the resulting edges do not reflect the same edges that will
be created, if the pre-order rule is applied one node at a time.

* `E := { e(n) | (n in N) }` where `e(n) := (lc(n),ns(n))`
* `lc(n)` allows to determine the node's (current) last child
* `ns(n)` allows to determine the node's next sibling

Note that, if the pre-order rule is first applied to `n`, then (if it had a
child node) `lc` will have a subsequent sibling (i.e. `ns`). As a matter of
consequence, `ns` must then be taken into account when the rule is applied
to `lc`.

Note that, if the pre-order rule is first applied to `lc`, then (if it had a
child node) `lc` will have a subsequent sibling. Because of that, and if the
pre-order rule would then be applied to node `n` next, `lc` would no longer
appear as the last child of node `n`.

**The pre-order rule must therefore be applied one node at a time.**

Even though all the edges that will be created must be determined dynamically,
subsequent discussions may still describe the application of the pre-order
rule (one node at a time) as **embedding the (set of) pre-order edges** into
the ordered doctree.

<!-- ======================================================================= -->
## the (preD <=> postR) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace such that both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`

Note that, due to this correspondence, the reversed post-order trace
is **order-reversing**.
