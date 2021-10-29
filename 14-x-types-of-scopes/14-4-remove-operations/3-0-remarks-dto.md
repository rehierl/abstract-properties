
<!-- ======================================================================= -->
# remarks

```
p -> fs .. ps -> n -|-> ns .. ls
                    |-> fc .. lc
```

Recall that the node order of an ordered document tree is such that no node in
it has more than two child nodes: (1) its former next subsequent sibling `ns`
and (2) its former first child `fc`. Furthermore, an ordered document tree is
itself, as a general node tree, an unordered tree (i.e. has itself no child
order). Because of that, one can strictly speaking not distinguish between both
child nodes. However, since the `Node` interface of a DOM tree has shortcut
properties, both child nodes can be distinguished from one another using the
`.nextSibling` and the `.firstChild` object properties.

Since both properties allow to distinguish one child from another, one can
restrict the type-2 scope of a node over the node order of an ordered document
tree. That is, both properties allow to define a **some-of** quantifier by
excluding one of the branches that begin in the corresponding child node,
each of which can be understood to define a proper subset its parent's type-2
scope (i.e. the type-2 scope of the corresponding child node).

Based on the above, the following examples will examine the effects of the
removal of a suffix over DTO while excluding one of the two branches.

Note that, in the context of removing nodes, excluding one branch from the
removal means to keep that branch. That is, the removal is restricted to
removing the defining node and the other branch.

<!-- ======================================================================= -->
## exlcude/keep both branches

```
before the removal                      after the removal
================================   =>   =====================================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps -> fc .. lc -> ns .. ls
                    |-> fc .. lc
```

Note that holding on to both branches corresponds with the removal of a node's
type-0 scope (i.e. only remove the defining node - suffix over DTR).

<!-- ======================================================================= -->
## exclude/keep the ns-branch - s(n)

```
before the removal                      after the removal
================================   =>   =========================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps -> ns .. ls
                    |-> fc .. lc
```

Note that hodling on the branch that is defined by `ns` corresponds with the
removal of a node's type-1 scope (i.e. remove the suffix over DTU).

<!-- ======================================================================= -->
## exlcude/keep no branch

```
before the removal                      after the removal
================================   =>   =================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps
                    |-> fc .. lc
```

Note that holding on to none of the two branches corresponds with the removal
of a node's type-2 scope (i.e. remove the suffix over DTO).

<!-- ======================================================================= -->
## exclude/keep the fc-branch - c(n)

```
before the removal                      after the removal
================================   =>   =========================
p -> fs .. ps -> n -|-> ns .. ls        p -> fs .. ps -> fc .. lc
                    |-> fc .. lc
```

Recall that, with the removal of a node one must also remove that node from the
corresponding child order. In addition to that, one needs to keep in mind that
each child order has a point of reference (i.e. the parent node). After all,
all the nodes in a child order are child nodes to the same parent node. Finally,
a parent node can not end up having to disjoint child orders. That is, the child
order of a node must be merged with the child order of the node's parent.
