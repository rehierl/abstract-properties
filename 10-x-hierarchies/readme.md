
# hierarchies

This meta chapter generalizes the concept of **hierarchies as sets-of-items**.

Each such set must satisfy certain requirements which are intended to guarantee
that such a hierarchy (aka. a setup of sets) can be understood to define a node
tree. In other words, node trees can be transformed into sets-of-items that must
have certain characteristics. The latter of which guarantee that the source tree
can be recreated from the set-of-items that was formed from it.

```
node-tree <-> a set-of-items
|<------ isomorphic ------>|
```

Note that neither a set-of-items, nor the items in it are required to be
hierarchical. The items in such a setup are however required to have certain
characteristic. The description as a "hierarchy" is therefore intended as
a reference to the **isomorphism** between a given set-of-items and the node
tree it defines. After all, the latter of which can be described as being
hierarchical.

```
(s <-> S), (T <-> S)
```

Recall that the introduction of the concept of abstract properties did mention
several **isomorphisms** between ordered sequences `s`, path graphs and total
orders such as orders that can be described as (total) families of scopes.
Likewise, this introduction did mention the isomorphisms between node trees `T`
and partial orders such as orders that can be described as (partial) families
of scopes. (Note that the former isomorphisms can be described as a specialized
case of the latter isomorphisms, and the latter as a general case of the former).
