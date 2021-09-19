
<!-- ======================================================================= -->
## flat documents, total orders

In the context of a document order, with no overall partial order embedded into
it (i.e. a flat document), one can still use the same approach to define types
of scopes. The only difference is that only two base orders are available: (1)
the documents trivial suborder (DTR), and (2) the total document order (DPR).

```
DTR ------> DPR
|< min   max >|
```

* DTR - the trivial document order
* DPR - the pre-order tree traversal

Note that the flat document can still be described as a node tree. After all,
the total document order is then defined as an ordered sequence of nodes which
corresponds with a simple path graph. Based on that, one can still describe the
document traversal as a pre-order traversal since the only difference is then
that every single node is then guaranteed to have no more than one subsequent
sibling/child.

```
n1 ... ni ... nk
|-t(T)-------->|
      |-t1---->|
      |--| t0
```

**t0, type-0:** The type-0 scope is restricted to the defining node. As such,
it contains none of the node's descenants (hence "type-0"). Note that this
scope can be described as the induced subtree `DTR[n]` over the forest of
root nodes DTR.

**t1, type-1:** The type-1 scope extends the type-0 scope by the additional
descendants in DPR. That is, the type-1 scope of node `ni` is the set of
nodes in the induced subtree/suffix `DPR[n]`.

<!-- ======================================================================= -->
## remarks

Note that DPR in the context of a flat document is equivalent to DTU in regards
to a hierarchical document. That is, it results from embedding the edges in the
document tree/path into the trivial suborder DTR.
