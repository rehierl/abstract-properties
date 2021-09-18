
<!-- ======================================================================= -->
# types of scopes

```
<r> ... <p> ... <n> c(n) </n> s(n) </p> s(p) ... </r>
|-t(T)--------------------------------------------->|
scope-t3(n)     |-t3------------------------------->|
scope-t2(n)     |-t2----------------->|
scope-t1(n)     |-t1------->|
scope-t0(n)     |-| t0
```

The following introduces the types of scopes a node has, based on the induced
subtrees over the appropriate base order, that have the node as their root.

```
|-t0[n]-|  |-t1[n]-----|  |-t[n]-----------|
|   n   |  | n =|=> fc |  | n=|=> fc .. lc |
|-------|  |    |=> .. |  |   |=> ns .. ls |
           |    |=> lc |  |----------------|
           |-----------|

|-t3[n]-------------------------------------|
| n => (fc .. lc ..) => (ns .. ls ..) => .. |
|-------------------------------------------|
```

**t0, type-0:** The type-0 scope is restricted to the defining node. As such,
it contains none of the node's descendants (hence "type-0"). Note that this
scope can be described as the induced subtree `DTR[n]` over the forest of
root nodes DTR.

**t1, type-1:** The type-1 scope extends the node's type-0 scope by the
node's descendants in DTU. As such, the type-1 scope of node `n` is the
set of nodes in the induced subtree `DTU[n]`.

**t2, type-2:** The type-2 scope extends the node's type-1 scope by the
additional descendants in DTO. That is, the type-2 scope of node `n` is
the set of nodes in the induced subtree `DTO[n]`.

**t3, type-3:** The type-3 scope extends the node's type-2 scope by the
additional descendants in DPR. That is, the type-3 scope of node `n` is
the set of nodes in the induced subtree/suffix `DPR[n]`.

<!-- ======================================================================= -->
## remarks

Note that the indexing of the types of scopes is in regards to the sets of
edges that have been embedded. That is, `t0` denotes that no set of edges
has been embedded, which is why the overall set of edges in the underlying
node order (i.e. DTR). With that in mind, `t1` denotes that the first set
of edges (i.e. the edges in DTU) has been embedded, `t2` that the doctree's
child order has been embedded, and `t3` that the pre-order rule has been
applied.

Note that the types of scopes, as introduced above, are such that the next
type is defined by including some of the nodes the previous type did not
cover. That is, these types build upon each other since they are defined
based on iteratively embedding non-conflicting sets of edges.

* `(t0(n) subset-of t1(n))`
* `(t1(n) subset-of t2(n))`
* `(t2(n) subset-of t3(n))`

Note that each scope can be understood to define a substring over the doctree's
pre-order trace DPR. with that in mind, scope-t0 can be described as a prefix
to scope-t1.

* `(t0(n) prefix-of t1(n))`
* `(t1(n) prefix-of t2(n))`
* `(t2(n) prefix-of t3(n))`

Note that each scope **begins with the start-tag** of node `n`. Also, a type-0
scope **ends with the start-tag** of the defining node (i.e. `<n>`), a type-1
scope **ends with the end-tag** of the defining node (i.e. `</n>`), a type-2
scope with the end-tag of its parent node (i.e. `</p>`), and a type-3 scope
with the end-tag of the doctree's root (i.e. `</r>`).

Note that, in regards to a particular defining node, one or more of the above
types of scopes may refer to the same set of nodes. For example, the first
three types of scopes are the same, if the defining node is a last child to
its parent in the unordered doctree.

Recall that the pre-order rule can not be understood such that it is based
upon a well-defined set of edges. In contrary to that, every other set of
edges can be described as being **well-defined**. That is, one can clearly
state which edges will be embedded when transitioning from one node order
to another.
