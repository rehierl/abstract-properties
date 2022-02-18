
# ordered document trees

Recall the introduction to document trees in "mathematics / node trees"
(i.e. chapter 05-02), which introduces critical **non-standard definitions**.

In order to guarantee consistent results over all implementations, the nodes
of a document tree must be processed one node at a time in a particular order.
Because of that, each document tree can be understood to be associated with a
specific trace of nodes `t` whose index order can be understood to apply to
the nodes in it. That is, the **document order** of a document tree can be
said to correspond with the index order over its trace of nodes.

Since each node is associated with a unique index in the document order, any
parent in a document tree can be understood to have a first child and a last
child. That is, any such parent, and therefore also the document tree, can
be understood to have a **child order** associated with it.

Based on the above, the child order of a parent `co(p)` can be described as an
subsequence to the document order (induced by its set of child nodes `c(p)`),
and the child order of a document tree `co(T)` as the set of all of these
subsequences.

* `co(p) := t[c(p)] := (c1..cZ)`
* `co(T) := { t[c(p)] | (p in PN) }`

However, since each sequence corresponds with a path graph, one should instead
imagine the child order of a document tree `CO(T)` as the union graph of all
the child orders of all the parent nodes in it, which allows to focus on a
joint set of Edges `E` that contains all the edges in each child order `co(p)`.

* `CO(N,E)` where `E := { e | (e in co(p)) and (p in PN) }`

With the above in mind, all the edges in the child order of a document tree
can be embedded into the set of edges of the unordered document tree `DTU(N,E)`.
What results is a graph that no longer satisfies the requirements of a node
tree since nodes may in general have more than one incoming edge and thus
more than one parent node. However, transitively reducing the extended set
of edges `TR(E)` will yield a new set of edges that does once again satisfy
the requirements of a node tree.

* `DTO(N,E)` where `E := TR( E(DTU) + E(CO) )`

Note that adding the edges of a child order to the edges of the unordered
document tree does not produce a conflict in the underlying node order (i.e.
no symmetric edges), which would break the underlying tree order. Furthermore,
and since each tree corresponds with an actual (partial) order relation over
its nodes, the subsequent transitive reduction can be described as a matter
of consequence.

```
DTU                 + CO          = DTO
========================================================================
         p          | embedding a |
         |          | child order | long pattern:
 -----------------  |             | p -> (fs .. ps) -> n -|-> (ns .. ls)
 | .. |  |  | .. |  |             |                       |-> (fc .. lc)
 fs  ps  n  ns  ls  |     =>      |
         |          |             | reduced pattern:      in short:
      -------       |             | n -|-> (ns .. ls)     n -|-> s
      | ... |       | a partial   |    |-> (fc .. lc)        |-> c
      fc   lc       | extension   |
```

Note that the overall transition from `DTU` to `DTO` can be described
as **an order embedding**. Also, the overall transition can be described
as **a (partial) extension** of the document tree's tree order.
After all, the node order of the ordered document tree is such that
**no node has more than two child nodes**, its former next sibling (ns)
and its former first child (fs).

Note also that the ordered document tree itself, even though the child order
of the document tree is embedded into it, still **has no child order**. That
is because no path can be formed in between a node's former next sibling and
its former first child.
