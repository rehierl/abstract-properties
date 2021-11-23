
# hierarchy of (sub-)strings

```
T <-> Hstr
```

A document tree (T) allows to form hierarchies of strings of nodes (Hstr) such
that the source tree can be recreated based on the relationships between the
strings within such a hierarchy.

Note that, in the context of this discussion, a string of nodes is an ordered
sequence of nodes, each of which corresponds with a path graph and as such
with a tree. Because of that, a hierarchy of strings may also be described
as a hierarchy of paths and also as a (specialized) hierarchy of trees.

Note that the introduction of hierarchies of strings (Hstr) must be understood
to be in preparation of more specific hierarchies of strings. Hierarchies of
rooted paths (Hr) and hierarchies of pre-order traces (Hpre -or- Hnci) are
examples of specific hierarchies of strings.

Note that a hierarchy of rooted paths can be understood as a partial setup
of strings such that the related-to operator is based on the **prefix-of**
operator, and sucht that the strings in it are either related ex-or overlap
each other (i.e. the **RE-OV** case). Furthermore, the CE of each string/path
is its last element.
