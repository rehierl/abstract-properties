
<!-- ======================================================================= -->
## summary, remarks

Embedding the child order of an unordered doctree into its tree order will ..

```
         p           | tree-order:
         |           | top-to-bottom oriented
 -----------------   | "ancestor-of"
 | .. |  |  | .. |   |
 fs  ps  n  ns  ls   | child-order:
         |           | left-to-right oriented
      -------        | "presequent-sibling-of"
      | ... |        |
      fc   lc        |
```

.. transform the tree order such that no node has more than two child nodes.

```
      presequent           subsequent   |  the reduced pattern    |
      siblings             siblings     |  of an ordered doctree  |  in short
 =====================================  |  ===================    |  ========
 p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> (ns .. ls)      |  n -|-> s
                       |-> (fc .. lc)   |     |-> (fc .. lc)      |     |-> c
                                        |                         |
                           child nodes  |                         |
```

Because of that, the embedding of a child order has the effect of reducing the
amount of incomparable nodes. That is, the resulting tree will in general have
fewer nodes for which no path can be formed such that it has these nodes as its
endpoints. Based on that, the embedding of a child order can be said to push a
tree order towards a total order, which is why embedding a child order into the
node order of a tree can be described as **a partial extension**.

Note that, the embedding of a child order will turn **leaf nodes**, which are
no last child to a parent, into parent nodes. Because of that, the embedding
of a child order will reduce the amount of leaf nodes that remain. However, the
embedding of a child order can not turn leaf nodes, which are the last child of
a parent, into parent nodes. Consequently, these nodes (e.g. `ls` and/or `lc`)
are the only candidates for leaf nodes in the resulting node order. Because
of that, the reduction in the amount of leaf nodes contributes to reducing the
amount of incomparable nodes.

Note that the child order of an unordered doctree will be embedded as a set of
**pre-determined edges**. That is, the embedding of the child order of a parent
has no side effect on the embedding of the child order of another parent. Hence,
the child orders of all parent nodes can be embedded in any order, which is why
no particular processing order is required.

<!-- ======================================================================= -->
# embedded suborders

```
      presequent           subsequent   |  the tree-order in
      siblings             siblings     |  regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Since node `n` in an ordered doctree is still subsequent to its former ancestors,
and also presequent to its former descendants, the tree order of the unordered
doctree can be said to be a sub-order to the tree order of the ordered doctree.
Because of that, the ordered doctree can be said to preserve the node order of
an unordered doctree.

* `n` is subsequent to its (former) ancestors
* `n` is presequent to its (former) child nodes
* The unordered doctree is a partial suborder to the ordered doctree.
* The rooted paths of the unordered doctree are total suborders.

Since each node `n` is still subsequent to its former presequent siblings, and
also still presequent to its former subsequent siblings, the child order that
was embedded into the unordered doctree is a suborder to the tree order of the
ordered doctree. Because of that, the ordered doctree can be said to maintain
the child order.

* `n` is subsequent to its (former) presequent siblings
* `n` is presequent to its (former) subsequent siblings
* The child orders of the unordered doctree are paths over the ordered doctree.

Furthermore, the former presequent siblings of node `n` are now ancestors to
node `n` in the ordered doctree. Likewise, the former subsequent siblings of
node `n` are now descendants to node `n`.

* nodes `fs` to `ps` are ancestors to `n`
* nodes `ns` to `ls` are descendants to `n`
* The former presequent siblings of each node are ancestors to these nodes.
* `(fs..ls)` is a total suborder to `rp(n)` (over the ordered doctree).

Note that `(fs..ls)` is not just some total suborder, but in fact an actual
substring to `rp(n)`. That is, the former presequent siblings of a node appear
as a sequence of consecutive nodes in its rooted path. Put differently, the
rooted path of a node in the ordered doctree is such that its former ancestors
are interlaved by substrings of presequent siblings.

Note that a node's former next sibling remains to be incomparable to its former
child nodes and its descendants. That is, one can still not form a path between
any of these nodes. Because of that, the ordered doctree itself still has
**no child order**.
