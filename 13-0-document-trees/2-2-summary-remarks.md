
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

Due to the above, the embedding of a child order has the effect of reducing the
amount of incomparable nodes. That is, the resulting tree will in general have
fewer nodes for which no path can be formed that has any of these nodes as its
endpoints. Based on that, the addition of a child order can be said to push or
stretch a tree order towards a total order, which is why embedding a child order
into the node order of a tree can be described as **a partial extension**.

Note that the child order of an unordered doctree will be embedded as a set
of **pre-determined edges**. That is, the embedding of the child order of one
parent has no side effect on the embedding of the child order of another parent.
Because of that, the child orders of all parent nodes can be embedded in any
order - i.e. no particular processing order is required.

<!-- ======================================================================= -->
## embedded suborders

Since node `n` is still subsequent to its former ancestors, and still presequent
to its former descendants, the tree order of the unordered doctree can be said
to be a sub-order to the tree order of the ordered doctree. Because of that, the
ordered doctree can be said to preserve the node order of an unordered doctree.

* `n` is subsequent to its (former) ancestors
* `n` is presequent to its (former) child nodes
* The unordered doctree is a partial suborder to the ordered doctree.
* The rooted paths of the unordered doctree are total suborders.

Since node `n` is still subsequent to its former presequent siblings, and still
presequent to its former subsequent siblings, the child order that was embedded
into the unordered doctree now is a suborder to the tree order of the ordered
doctree. Because of that, the ordered doctree can be said to maintain the child
order.

* `n` is subsequent to its (former) presequent siblings
* `n` is presequent to its (former) subsequent siblings
* The child orders of the unordered doctree are total suborders.

Furthermore, the former presequent siblings of node `n` are now ancestors to
node `n` in the ordered doctree. Likewise, the former subsequent siblings of
node `n` are now descendants to node `n`.

* nodes `fs` to `ps` are ancestors to `n`
* nodes `ns` to `ls` are descendants to `n`
* The former presequent siblings of each node are ancestors to these nodes.
* `(fs..ls)` is a total suborder to `rp(n)`

Note that `(fs..ls)` is not just some total suborder, but in fact an actual
substring to `rp(n)`. That is, the former presequent siblings of a node appear
as a sequence of consecutive nodes in its rooted path. Put differently, the
rooted path of a node in the ordered doctree such that its former ancestors
are interlaved with substrings of presequent siblings.

Note that a node's former next sibling remains to be incomparable to its former
child nodes and its descendants. That is, one can still not form a path between
any of these nodes. Because of that, the ordered doctree has itself still
**no child order**.
