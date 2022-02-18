
<!-- ======================================================================= -->
# summary, remarks

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

.. transform the tree order such that **no node has more than two child nodes**.

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
fewer pairs of nodes for which no path can be formed which has these nodes as
its endpoints. Based on that, the embedding of a child order can be understood
to push a tree order towards a total order, which is why the embedding of a
child order into the node order of a tree can be described as
**a partial extension**.

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
has no side effect on the embedding of the child order of another parent (such
as the siblings of the corresponding parent). Hence, the child orders of all
parent nodes can be embedded in any order, which is why no particular processing
order is required.
