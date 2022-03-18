
# document traversal / ordered document trees

```
DTU                 + CO           = DTO
=========================================================================
         p          | embed the    |
         |          | child order  | long pattern:
 -----------------  |              | p -> (fs .. ps) -> n -|-> (ns .. ls)
 | .. |  |  | .. |  |              |                       |-> (fc .. lc)
 fs  ps  n  ns  ls  |      =>      |
         |          |              | reduced pattern:      in short:
      -------       |              | n -|-> (ns .. ls)     n -|-> s
      | ... |       | a partial    |    |-> (fc .. lc)        |-> c
      fc   lc       | extension    |
```

Recall the introduction of document trees in "mathematics / node trees"
(chapter 05-2), which introduced essential **non-standard definitions**.

In order to guarantee consistent results over all implementations, a document
tree must be processed one node at a time in a specific order. Because of
that, each document tree can be understood to be associated with a specific
trace of nodes `t` whose index order can be understood to apply to the nodes
in it. That is, the **document order** of a document tree can be understood
to correspond with the index order over its trace of nodes.

Since each node is associated with a unique index in the document order, any
parent in a document tree can be understood to have a first child (lowest
index) and a last child (greatest index). Based on that, any parent, and thus
also the entire document tree, can be understood to have a **child order**
associated with it.

The child order of a parent `co(p)` can be described as a subsequence to the
document order, which is induced by its set of child nodes `c(p)`. Based on
that, the child order of a document tree `co(T)` can be described as a set
of all of these subsequences.

* `co(p) := t[c(p)] := (c1..cZ)`
* `co(T) := { co(p) | (p in PN) }`

However, since each sequence corresponds with a path graph, one should instead
imagine the child order of a document tree `CO(T)` as the union graph of all
the path graphs `CO(p)` of each child order `co(p)` in a document tree. This
point of view allows to focus on a joint set of Edges `E` that contains all
the edges in each child order `CO(p)`.

* `CO(N,E)` where `E := { e | (e in CO(p)) and (p in N) }`

With that in mind, the edges in the child order of a document tree can be
embedded into the set of edges of **the unordered document tree (DTU)**.
What results is a graph that no longer satisfies the requirements of a node
tree since some of the nodes will then have more than one incoming edge and
therefore more than one parent.

However, transitively reducing the extended set of edges will yield a new set
of edges `TR(E)` which satisfy the requirements of a node tree. The resulting
node tree will be referred to as **the ordered document tree (DTO)**.

* `DTO(N,E)` where `E := TR( E(DTU) + E(CO) )`

<!-- ======================================================================= -->
## remarks

Note that embedding the edges of a child order into the unordered document
tree does not produce a conflict in the underlying node order (i.e. there
will not be any symmetric edges), which would break the underlying tree order.
Furthermore, and since each tree corresponds with a (partial) order relation
over its nodes, the subsequent transitive reduction can be described as a
necessity.

Note that the overall transition from `DTU` to `DTO` can be described as
**an order embedding** since the doctree's child order is then embedded into
the doctree's tree order. Furthermore, and since the resulting tree order is
in general no total order, the overall transition can be described as
**a partial extension** of said tree order. This in contrary to
**a linear extension** which always results in a total order.

Note that the node order of an ordered document tree is such that
**no node in it has more than two child nodes**,
its former next sibling (ns) and its former first child (fs).

Note that the ordered document tree itself itself, even though the child order
of the document tree is embedded into it, still **has no child order**. That
is because even in DTO, no path can be formed from one child to its sibling
(i.e. between a node's former next sibling and its former first child).
