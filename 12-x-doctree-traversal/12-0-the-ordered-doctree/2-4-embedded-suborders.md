
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

Since node `n` in an ordered doctree (DTO) is still subsequent to its former
ancestors, and also presequent to its former descendants, the tree order of
the unordered doctree (DTU) can be said to be a sub-order to the tree order
of the ordered doctree. Because of that, the ordered doctree can be said to
preserve the node order of an unordered doctree - i.e. DTO is order-preserving
in regards to DTU.

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
substring to the rooted path `rp(n)` over the ordered doctree. That is, the
former presequent siblings of a node appear as a sequence of consecutive
nodes in its rooted path. Put differently, the rooted path of a node in the
ordered doctree is such that its former ancestors are interlaved by substrings
of presequent siblings.

Note that a node's former next sibling remains to be incomparable to its former
child nodes and its descendants. That is, one can still not form a path between
any of these nodes. Because of that, the ordered doctree itself still has
**no child order**.
