
# hierarchy of (sub-)strings

```
T <-> Hstr
```

A tree (T) allows to form hierarchies of strings of nodes (Hstr) such that the
source tree can be recreated based on the relationships between the strings in
such a hierarchy.

Note that, in the context of this discussion, a string of nodes is an ordered
sequence of nodes, each of which corresponds with the path over an acyclic
graph and as such satisfies the requirements of a tree. Because of that, a
hierarchy of strings may also be described as a hierarchy of paths and even
as a (specialized) hierarchy of trees.

Note that the introduction of hierarchies of strings (Hstr) can be understood
as an attempt to simplify the process of defining more specific hierarchies of
strings. Hierarchies of rooted paths (Hrp) and hierarchies of pre-order traces
(Hpre, or Hnci) are examples of such specialized hierarchies.

Note that at this point, a generic type of hierarchy of strings is such that
there is no requirement as to how the strings a hierarchy contains must be
formed. Because of that, the definition of specialized hierarchies will have
to specify the kinds of strings they contain, and how these must be related
with each other.
