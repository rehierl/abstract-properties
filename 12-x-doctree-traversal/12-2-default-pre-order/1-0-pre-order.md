
<!-- ======================================================================= -->
# the (default) pre-order tree traversal (D)

```js
//- the default pre-order traversal
traverseInPreOrderD(node) {
  //- visit the node and enter its scope
  visit(node);

  //- recursively visit all child nodes
  for(child in node.childNodes) {
    traverseInPreOrderD(child);
  }

  //- exit the node's scope
}
```

Note that the pre-order trace will contain the nodes in tree order (i.e.
ancestors before descendants) and also in child order (if one does exist).
As such, the pre-order trace is **order-preserving**.

```
      presequent           subsequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> (ns .. ls)      |  n -|-> s
                       |-> (fc .. lc)   |     |-> (fc .. lc)      |     |-> c
                                        |                         |
                           child nodes  |                         |
```

Note that the pre-order traversal first embeds a child order, even if only
temporary, and then appends the sequence of subsequent siblings `s(n)` to
the sequence of child nodes `c(n)` - i.e. `(n × c × s)`.

```
n -|-> (ns .. ls)     =>     -> n × (fc .. lc ..) × (ns .. ls ..)
   |-> (fc .. lc)
```

Note that the pre-order rule can be understood such that it defines a new
sequence of nodes which replaces the node and all the nodes subsequent to it.
Based on that it can be understood to define how to restructure the tree in
regards to some current node `n`.

<!-- ======================================================================= -->
## order of execution

Since the pre-order rule is such that a node and all of its descendants form
a substring to the trace of a tree, **no particular order of execution**
is required. That is, even though the root of a tree will in general be used
as the starting point, one can apply the pre-order rule in any order and still
end up with the same trace of nodes.

(Think in terms of linked lists, not in terms of actual sequences/arrays).

<!-- ======================================================================= -->
## (set of) pre-order edges (?)

The pre-order rule allows to pre-calculate a set of edges that can be understood
to be embedded into the ordered document tree. However, as can be seen below,
the resulting edges do not reflect the same edges that will be created, if the
rule is applied one node at a time.

* `E := { e(n) | (n in N) }` where `e(n) := (lc(n),ns(n))`
* `lc(n)` the node's current last child
* `ns(n)` the node's current next sibling

Note that, if the pre-order rule is first applied to `n`, then `lc` will have
`ns` as its next subsequent sibling. Because of that, `ns(lc)` will return `ns`
if the pre-order rule is applied to `lc` next.

Note that, if the pre-order rule is first applied to `lc`, then `lc` has no
subsequent sibling. Because of that, and if the pre-order rule would then be
applied to node `n` next, `lc` would no longer be the last child of `n` since
this last child would then be the former last child of `lc`.

Even though the edges that will be created may differ depending on how the rule
is applied, subsequent discussions will describe the application of the rule as
**embedding the (set of) pre-order edges** into the ordered doctree, while
referring to the above pre-calculated set of edges.

<!-- ======================================================================= -->
## the (preD <=> postR) correspondence

Note that the default pre-order trace of a tree corresponds with the reversed
post-order trace. That is because both traces are reversed to each other.

* `preD(n) := n × (fc .. lc ..)`
* `postR(n) := (.. lc .. fc) × n`
* `preD(T)` is reversed to `postR(T)`

Note that, due to this correspondence, the reversed post-order trace
is **order-reversing**.
