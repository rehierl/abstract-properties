
<!-- ======================================================================= -->
# types of properties

```
... <n> c(n) </n> s(n) </p> s(p) ... </r>
|-t(T)--------------------------------->| - enter/exit a document
t0  |-|                                   - enter/visit/exit a node
t1  |-(scope)-->|                         - enter/exit a type-1 scope
t2  |-(extended scope)--->|               - enter/exit a type-2 scope
t3  |-(unrestricted scope)------------->| - enter/exit a type-3 scope
```

One can assume that there are no more than four types of abstract properties,
each of which is defined based on the corresponding scope. Because of that,
a type-x property can be understood to be defined such that its scope is the
type-x scope of its defining node.

* **a type-x property is a property with a type-x scope**

Note that these scopes need to be seen as "default scopes". That is, depending
on a given context (e.g. rank values) it may or may not be possible to restrict
a property's scope to a prefix of its default scope.

* **extensions may or may not restrict the default scope to a prefix**

<!-- ======================================================================= -->
## box-/line-based visualizations

```
     |-s-----|       |-u-------------|      | - a pre-order trace,
     |   |-t-|---|   |   |-v-----|   |      | - including the scopes of
( n1,|n2,|n3,|n4,|n5,|n6,|n7, n8,|n9,|n10 ) | - properties s, t, u, and v
     |---|---|   |   |   |-------|   |      |
         |-------|   |---------------|      |
```

Since each node may be associated with more than one property, the scopes
of distinct properties can in principle be disjoint (e.g. `s` and `u`),
related (e.g. `u` and `v`), or even overlap each other (e.g. `s` and `t`).

```
( n1, n2, n3, n4, n5, n6, n7, n8, n9, n10 ) | - a pre-order trace
     -s------        -u--------------       | - properties - s, u
         -t------        -v------           | - properties - t, v
```

Similar as before, the scopes of multiple properties can be visualized by
underlining all the nodes in their scopes (i.e. a continuous line per scope).
Based on that, the relationships between the scopes can be determined with
ease. Furthermore, and for the purpose of clarification, property identifiers
may be used as shown above.

<!-- ======================================================================= -->
## type-0 properties

```
type-0 property                   in an ordered doctree
==========================        =====================
<n property="value">              |-s0-|
  [ descendants excluded ]        | n -|-|-> fc .. lc
</n>                              |----| |-> ns .. ls
```

A type-0 property is defined to only apply to its defining node. That is, such
a property is defined to have no effect on any of the descendants of a defining
node (e.g. **an id attribute**). Because of that, the scope of a type-0 property
contains one node only, the property's defining node.

Note that any such scope begins with the defining node's start-tag and ends
with the defining node's start-tag. As such, a type-0 property is the only type
of property whose scope ends with a start-tag while still including the node
of that tag.

Note that descendants can still be said to be subsequent and therefore related
to all the properties of its ancestors. That is because these nodes are located
on the rooted paths of such descendants (i.e. subsequent-to). Based on that,
descendants can always be understood to be **(structurally) related** to all
the properties of their ancestors, regardless of what type these properties
are. Despite that, the property's definition is still the deciding factor if
a node counts towards the property's scope or not.

<!-- ======================================================================= -->
## type-1 properties

```
type-1 property                   in an ordered doctree
==========================        =====================
<n property="value">              |-s1--------------|
  [ descendants included ]        | n -|-> fc .. lc |
</n>                              |----|------------|
                                       |-> ns .. ls
```

A type-1 property is defined to also apply to all the descendants in the
unordered doctree (e.g. **a hidden attribute**). Because of that, the default
scope of such a property ends with the defining node's end-tag.

That is, type-1 properties are such that their scopes match the scope of the
defining node's pair of tags (i.e. start- to end-tag). The tags of a node
therefore enclose all the nodes in the default scope of a type-1 property
that has the node as its defining node.

Based that, one might assume that type-1 properties will be the predominant
type of properties since a node's pair of tags can be said to highlight the
corresponding scope. (Apart from that, there also is the widespread issue of
describing "unordered trees" as "ordered trees").

Note that future extensions may or may not be allowed to restrict the default
scope of a type-1 property. If a restriction can not be allowed, then the
scope of such a property will always be its default scope.

<!-- ======================================================================= -->
## type-2 properties

```
type-2 property                   in an ordered doctree
============================      =====================
  ...                             |-s2--------------|
  <n property="value">            | n -|-> fc .. lc |
    [ descendants included ]      |    |-> ns .. ls |
  </n>                            |-----------------|
  [ siblings included ]
</p>
```

A type-2 property is defined to also apply to all the additional descendants
(i.e. the former subsequent siblings and their descendants) in the ordered
doctree. Because of that, the default scope of such a property ends with the
end-tag of the defining node's parent in the unordered doctree.

Note that these types of scopes could in general be used to define (e.g.)
**(extended) hidden attributes** and **headings**.

<!-- ======================================================================= -->
## type-3 properties

```
type-3 property                   in a doctree's pre-order trace
==============================    ==================================
    ...                           |-s3-----------------------------|
    <n property="value">          | .. <n> .. </n> .. </p> .. </r> |
      [ descendants included ]    |--------------------------------|
    </n>
    [ siblings included ]
  </p>
  [ siblings of ancestors ]
</r>
```

A type-3 property is defined to also apply to all the additional descendants
in the document's pre-order trace. Because of that, the default scope of such
a property ends with the end-tag of the document's root.

Note that, since a type-3 scope ends with the last node of a tree's pre-order
trace, a type-3 scope may be referred to as having an **unrestricted** scope.
After all, there are no more nodes subsequent to the last node of a type-3
scope.

Note that, as mentioned before, type-3 scopes introduce the possibility of
**overlapping scopes**. Recall also that it is not possible to group the
nodes in the intersection of overlapping scopes using a pair of tags.
