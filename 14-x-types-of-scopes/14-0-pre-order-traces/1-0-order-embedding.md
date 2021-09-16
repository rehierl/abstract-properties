
<!-- ======================================================================= -->
# embedded suborders

```
DTR --> DTU --> DTO --> DPR
|< minimal       maximal >|
```

Recall that embedding a child order into the unordered doctree (DTU) will yield
the ordered doctree (DTO). After that, applying the pre-order rule to the DTO
(i.e. embedding the pre-order edges into it) will yield the doctree's pre-order
trace, which can be said to correspond with the **processing order** (DPR).

With these processing steps in mind one can assume the **trivial suborder**
(DTR) (i.e. the document's set of nodes, but with an empty set of edges) as the
actual starting point of the above linear extension. That is, one begins with
the trivial suborder, and embeds all the edges in the unordered doctree into it.

A trivial order may be described as **minimal** since it does not define any
structure (aka. maximal disorder/entropy). That is "minimal" must be understood
to be in regards to the amount of edges that have been embedded into an order.
Conversely, a processing order can be described as **maximal** since the "order"
of a total order can not be increased any further.

* a trivial order has minimal "order"
* a total order has maximal "order"

<!-- ======================================================================= -->
## pattern-based overview

Recall that the above node orders can be described using the following
pattern-based descriptions. (Note that the trivial order only consists
of a simple set of nodes, which is why it won't be visualized).

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

Recall that an unordered doctree is such that no child order has been embedded
into it. Because of that, an unordered doctree must be treated like any other
node tree - i.e. with no child order attached to it.

```
      presequent           subsequent   |  the resulting tree-order
      siblings             siblings     |  in regards to node (n)
                                        |
p -> (fs .. ps) -> n -|-> (ns .. ls)    |
                      |-> (fc .. lc)    |
                                        |
                           child nodes  |
```

Recall that, embedding the doctree's child order into its tree order has the
effect of reducing the amount of child nodes to no more than two. Because of
that, each node has its former next subsequent sibling and its former first
child as its child nodes.

```
-> n -> (fc .. lc ..) -> (ns .. ls ..)
```

Recall that applying the pre-order rule has the effect of turning the ordered
doctree into a path graph and thus into the doctree's pre-order trace.
