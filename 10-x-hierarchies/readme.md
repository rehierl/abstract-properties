
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
characteristic. The description as a "hierarchy" is therefore intended as a
reference to the isomorphism between a given set-of-items and the node tree
it defines. After all, the latter of which can be described as being
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

```
T <-> Ht <-> Hs
|<----------->|
```

This meta chapter builds upon the isomorphisms mentenioned by the introduction
of abstract properties. That is, the isomorphism between a tree (T) and an
order of scopes is formalized as a hierarchy of scopes (Hs, the **T-Hs**
isomorphism). Similar to that, the isomorphism between a tree (T) and a
hierarchy of induced subtrees (Ht, the **T-Ht** isomorphism) is formalized.
As a matter of consequence, a hierarchy of scopes can be said to be isomorphic
to a hierarchy of trees (the **Ht-Hs** isomorphism).

```
T <-> Hrp <-> Hrs
|<------------>|
```

Variations in the definiton of hierarchies of things allow to formalize the
isomorphisms between a tree (T) and a hierarchy of reversed scopes (Hrs, the
**T-Hrs** isomorphism). Similar to that, the isomorphism between a tree
(T) and a hierarchy of rooted paths (Hrp, the **T-Hrp** isomorphism) can be
formalized. And just as before, a hierarchy of reversed scopes can be said to
be isomorphic to a hierarchy of rooted paths (the **Hrp-Hrs** isomorphism).

Note that the isomorphism between a hierarchy of scopes (Hs) and a hierarchy of
reversed scopes (Hrs, the **Hs-Hrs** isomorphism) is a matter of consequence.
Based on that, Hs can be considered to be **dual** to Hrs, and vice versa.
