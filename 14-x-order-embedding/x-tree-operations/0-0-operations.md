
<!-- ======================================================================= -->
# Operations on node trees

Hiding a node in a tree is similar to removing that node from the tree. After
all, the removed nodes can still be re-added, if the nodes are to be re-displayed.
The following will therefore focus on the removal of a node from a tree.

interdependent scopes
- relationships between scopes

In general, a scope can be restricted to a single node. If only there would
not be the following issue: What does it mean if the to-be-removed node has
a characteristic that is considered to also apply to its descendants
(e.g. a specific color)?

After all, once that node was removed, such a characteristic can no longer
apply to its former descendants. (How could it, if these bits of information
are to be removed along with the node?). The removal of a node may therefore
have unintended side effects, if the operation is restricted to a single node.

Based on that we can state that there are in general two different types of
scopes: (0) those that are restricted to a single node, excluding the node's
descendants (none of), and (1) those that contain a node, including and all
of its descendants (all of).

Note that a scope that is defined based upon **alternative X** is said to be
a **type-X scope**. That is, a type-0 scope is restricted to a single node,
whereas a type-1 scope also includes all of its descendants. Note also that
an operation may be referred to as a **type-X operation**, if its scope is
defined accordingly. (If required, a "type-X" term may even be reduced to a
simple **tX** or **sX** reference).

Note that, in the context of node trees, type-1 scopes can be understood to
define subgraphs, which are in general referred to as **induced subtrees**.
That is, groups of nodes can be used to form subtrees which contain all the
nodes in these groups and all the edges in between those nodes. As such
induced subtrees can be understood to reflect the scopes of graph-based
operations (i.e. remove all the nodes and edges that are included).

And here is the issue: What does "its descendants" refer to? The descendants
of a node before or after the addition of a child order to an unordered tree
`UT`? After all, the subsequent siblings of a node then count as (additional)
descendants in the resulting ordered tree `OT`.

Based on that, the definition of scopes can be clarified:

```
type-0 scope                  type-1 scope (UT)         type-2 scope (OT)
=========================     =====================     =====================
|-t0[n]-|                     |-t1[n]-------------|     |-t2[n]-------------|
|   n   | =|=> (fc .. lc)     | n =|=> (fc .. lc) |     | n =|=> (fc .. lc) |
|-------|  |=> (ns .. ls)     |----|--------------|     |    |=> (ns .. ls) |
                                   |=> (ns .. ls)       |-------------------|
```

* A **type-0** scope is restricted to the defining node.
* A **type-1** scope contains a node and all of its descendants in `UT`.
* A **type-2** scope contains a node and all of its descendants in `OT`.

```
type-3 scope in a tree's pre-order trace (PT)
=====================================================
        |-t3[n]-------------------------------------|
r => .. | n => (fc .. lc ..) => (ns .. ls ..) => .. |
        |-------------------------------------------|
```

* A **type-3** scope contains a node and all of its descendants in `PT`.

Note that this type system starts at "0" since a section, which only contains a
sectioning node, won't be of much use. That is because a section is intended to
group content. Also, "0" can be understood as "contains none of its descendants"
(i.e. neither in `UT`, nor in `OT`). With that in mind, "1" can be understood
to be in regards to `UT`, "2" to be in regards to `OT` (i.e. all the descendants
in an ordered tree), and finally "3" to be in regards to a tree's pre-order
trace.
