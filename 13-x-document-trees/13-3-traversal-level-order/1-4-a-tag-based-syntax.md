
<!-- ======================================================================= -->
## a tag-based syntax

```
n -|-> (ns .. ls)
   |-> (fc .. lc)
```

Since the child order of a node `co(n)` is a substring to a tree's level-order
trace, each child order represents and unit of consecutive nodes. As with the
pre-order trace, one can therefore inject tag-based markers to denote the
beginning and the end of a child order by prefixing the node's sequence of
former child nodes with a start-tag `<tag>` and by suffixing it with an
end-tag `</tag>`.

```
n -|-> (ns .. ls)
   |-> <tag> (fc .. lc) </tag>
```

If the level-order rule is then applied to node `n`, its "current" sequence of
subsequent siblings will be suffixed with its modified sequence of child nodes.

```
n × (ns .. ls) × (<tag> fc .. lc </tag>)
```

Note that, at this point, each tag represents nothing more but the beginning
and the end of a child order. Because of that, applying the level-order rule
to a tag can not have any effect since tags act as specialized leaf nodes
(i.e. no child nodes of their own).

<!-- ======================================================================= -->

```
seq(T) := (r, <tag>, fc, .., lc, </tag>, ..)
```

As before, and since the level-order rule will also be applied to every other
node in the tree, the tree's level-order trace will be transformed into a
bloated sequence of nodes and tags.

Note that, since the tree's root effectively represents a 1-node child order,
one can think of the tree's root as being prefixed and suffixed with its own
pair of tags (i.e. `(<tag>, r, </tag>)`).

However, in contrary to a tree's pre-order trace, the start-tag of the child
order of a non-root parent will have the end-tag of a presequent child order
as its next presequent item. Because of that, a node and its child order are
not adjacent to each other in a tree's level-order trace.

Consequently, a node can neither be pushed into the start-tag of its child
order, nor into the corresponding end-tag. Because of that, a level-order
trace will remain to be **a mixed sequence of** node definitions (e.g. a
node reference) and tags. That is, unlike a pre-order trace, a level-order
trace can in principle not be represented as a pure sequence of tags.

Despite that, an open issue is that a parser could not detect to which parent
the nodes in a child order belongs. However, each start tag can be extended by
an attribute such that it provides **a reference to the parent** node of the
corresponding child order. Based on that, one can then recreate the tree from
a mixed sequence of nodes and tags.

```
seq(T) := (r, <tag p="r">, fc, .., lc, </tag>, ..)
```

Note that the reference attribute can be understood as an abstract property
that applies to each node in the corresponding child order. Likewise, the
attribute can be understood to represent a single edge (i.e. `(p,fc)`) or
one edge per child (i.e. `(p,ci)`).

Note that, based on the above attribute, a particular order of execution is in
principle no longer required. That is, child orders may appear in any order.

Note that the tree's level-order trace is still embedded as a suborder to the
mixed sequence of nodes and tags. That is, the tree's level-order trace can be
formed from it by simply dropping all the tags. Because of that, the mixed
sequence can still be said to correspond with the **level-order visit order**
of the nodes in a document tree.

<!-- ======================================================================= -->

At this point one can note that the root of a tree is unique such that it can
be described as the only child of some theoretical super-root (e.g. `R`). That
is, a tree's root can be expressed as **a merged pair of tags**.

```
seq(T) := (<r p="R"></r>, <tag p="r">, fc, .., lc, </tag>, ..)
```

Based on that, one can replace each node with such a pair of tags, which is
why the start- and end-tags of each child order is no longer required. After
all, each node then has its own parent reference.

```
seq(T) := (<r p="R" />, <fc p="r" />, .., <lc p="r">, ..)
```

Note that the resulting sequence is now such that each entry represents a
node definition that is extended by a reference to the corresponding parent.
Furthermore, consecutive nodes that have the same parent reference mark all
those child nodes which belong to the same child order.

Note that the overall transition from grouped child nodes towards isolated nodes
that are marked with a parent reference reflects **the overall issue** of how
to embed the child order of a parent (i.e. complex edges resolved into simple
2-element edges) into the tree's formal definition. In other words, complex
edges do not add anything substantial since each complex edge is equivalent
to a collection of simple edges.

Note that the underlying issue is such that, unlike with the pre-order trace,
a level-order trace **does not embed hierarchical groups** of consecutive nodes.
After all, the child orders embedded into it are all disjoint to each other.
Because of that, end-marker tags are not required since there are effectively
no groups of nodes that are embedded into each other.
