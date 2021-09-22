
<!-- ======================================================================= -->
# types of scopes

```
.......... <n> c(n) </n> s(n) </p> .. </r>
|-t(T)---------------------------------->|
type-3(n)  |-t3------------------------->| - over DPR
type-2(n)  |-t2----------------->|         - over DTO
type-1(n)  |-t1------->|                   - over DTU
type-0(n)  |-| t0                          - over DTR
```

The following introduces the types of scopes a node has, based on the induced
subtrees over the appropriate base order, that have the node as their root.

```
|-DTR---|  |-DTU-----------|  |-DTO------------|
|   n   |  | n -> fc .. lc |  | n-|-> fc .. lc |
|-------|  |---------------|  |   |-> ns .. ls |
                              |----------------|

|-DPR---------------------------------------|
| n -> (fc .. lc ..) -> (ns .. ls ..) -> .. |
|-------------------------------------------|
```

**t0, type-0:** The type-0 scope is restricted to the defining node. As such,
it contains none of the node's descendants (hence "type-0"). Note that this
scope can be described as the induced subtree `DTR[n]` over the forest of
root nodes DTR.

**t1, tU, type-1:** The type-1 scope extends the node's type-0 scope by the
node's descendants in DTU. As such, the type-1 scope of node `n` is the set
of nodes in the induced subtree `DTU[n]`.

**t2, tO, type-2:** The type-2 scope extends the node's type-1 scope by the
additional descendants in DTO. That is, the type-2 scope of node `n` is the
set of nodes in the induced subtree `DTO[n]`.

**t3, type-3:** The type-3 scope extends the node's type-2 scope by the
additional descendants in DPR. That is, the type-3 scope of node `n` is
the set of nodes in the induced subtree/suffix `DPR[n]`.

<!-- ======================================================================= -->
## remarks

Note that the indexing of the types of scopes is in regards to the sets of
edges that have been embedded. That is, `t0` denotes that no set of edges has
been embedded, which is why the overall set of edges in the underlying node
order (i.e. DTR). With that in mind, `t1` denotes that the first set of edges
(i.e. the edges in DTU) has been embedded, `t2` that the doctree's child order
has been embedded, and `t3` that the pre-order rule has been applied.

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

Note that, in regards to a particular defining node, one or more types of
scopes of the same node may denote the same set of nodes. For example, the
first three types of **scopes are equal**, if the defining node is a last
child to its parent in the unordered doctree.

Recall that the pre-order rule can not be understood such that it is based on
a well-defined set of additional edges. In contrary to that, every other set
of edges can be described as being **well-defined**. That is because, one can
clearly state which edges will be embedded when transitioning from one node
order to another. Despite that, the document order itself can still be said
to be well defined (e.g. in terms of the corresponding tag soup).

<!-- ======================================================================= -->
## terminology

```
... <n> c(n) </n> s(n) </p> .. </r>
|-t(T)--------------------------->| - enter/exit the document
t0  |-|                             - enter/visit/exit the node
t1  |-(scope)-->|                   - exit its (type-1) scope
t2  |-(extended scope)--->|         - a type-2 exit
t3  |-(unrestricted scope)------->| - a type-3 exit
```

With the above types of scopes defined one can now use descriptions such as
**the type-x scope of node y** in order to denote the corresponding scope of
the specified node. Likewise, the above definitions allow to refer to the
descendants of a node in regards to a particular order by using descriptions
such as **the type-x descendants of node y**.

Thus far the description **the scope of a node** was mainly used to refer to
the type-1 scope of that node. This description may still be used as such,
which is why that description continues to be, first and foremost in regards
to the node order of the unordered document tree (DTU).

The less cryptic description **the extended scope of a node** may be used to
refer to the type-2 scope of a node. That is, this description is in regards
to the scope of that node in the ordered document tree (DTO).

Likewise, the description **the unrestricted scope of a node** may be used to
refer to the type-3 scope of a node. That is, this description is in regards
to the scope of that node in the total document order (DPR).

Note that **a node is being entered** if any of its scopes are being entered.
Despite that, one can use descriptions such as **the type-x enter-event** in
order to refer to the process of entering the corresponding scope.

Note that **a node is being exited** only if its type-0 scope is being exited.
Despite that, one can use descriptions such as **the type-x exit-event** in
order to refer to the process of exiting the corresponding scope.

* "enter a node" => enter its (t0, t1, t2, t3) scope
* "exit a node" => (only) when exiting its type-0 scope
* "visit a node" => (only) when processing its t0 scope
* "enter/exit the scope of a node" => enter/exit its t1 scope

Note that a node is being **entered**, **visited** and **exited** (each of
which is in regards to the node's type-0 scope) while no other node is in the
process of being entered, visited and exited (i.e. **an atomic operation**).
That is because all the type-0 scopes of all the nodes in a doctree are
pairwise disjoint, which is why all nodes will be visited one after another
in a strict orderly fashion. After all, each type-0 scope only consists of
the corresponding node.
