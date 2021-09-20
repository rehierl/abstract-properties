
<!-- ======================================================================= -->
## types of properties

```
type-0 property                   in an ordered tree
=========================         ===================
<n property="value">              |-s0-|
  [ descendant excluded ]         | n -|-|-> fc .. lc
</n>                              |----| |-> ns .. ls
```

A **type-0 property** can be defined to only apply to its defining node. That
is, such a property is in general defined to have no effect on the descendants
of a defining node (e.g. the "id" attribute). Because of that, the scope of a
type-0 property contains one node only, the property's defining node.

Note that descendants can still be said to be subsequent and therefore related
to the properties of its ancestors. That is because these nodes are located on
the rooted paths of such descendant nodes (i.e. subsequent-to). Based on that,
descendants can always be understood to be **(structurally) related to all the
properties of their ancestors**, regardless of what type these properties are.

Note that, one may distinguish between **soft/voluntary and hard restrictions**.
In other words, a restriction may be referred to as being "hard", if no further
descendants exist that could be affected. Based on that, the scope of a type-0
property can be said to be voluntarily restricted since the property's defining
node may in general have any number of descendants.

```
type-1 property                   in an ordered tree
==========================        ===================
<n property="value">              |-s1--------------|
  [ descendants included ]        | n -|-> fc .. lc |
</n>                              |----|------------|
                                       |-> ns .. ls
```

A **type-1 property** can be defined to also apply to all the descendants in
an un-ordered tree (e.g. the "hidden" attribute).

As before, a type-1 definition is no hard restriction since further nodes
subsequent to the defining node of a type-1 property can also be understood
to count towards the descendants of a defining node. (Recall that, in the
node order of an ordered tree, former subsequent siblings are descendants
to their former presquent siblings).

Note that type-1 properties are such that their scopes match the scope of the
defining node's tag (i.e. start- to end-tag). Because of that, a tag encloses
all the nodes in the scope of a type-1 property, if the property's defining
node is also the tag's defining node. Because of that, one in general needs to
distinguish between the scope of a tag/container and the scope of a property.

```
type-2 property                   in an ordered tree
============================      ===================
  ...                             |-s2--------------|
  <n property="value">            | n -|-> fc .. lc |
    [ descendants included ]      |    |-> ns .. ls |
  </n>                            |-----------------|
  [ siblings included ]
</p>
```

A **type-2 property** can be defined to also apply to all the additional
descendants (i.e. the former subsequent siblings and their descendants)
in the node order of an ordered tree (e.g. not in use?).

Note that these types of scopes could in general be used to define the scope
of a "hidden" attribute and also the scopes of headings such as "h1,..,h6"
(i.e. the scopes of section properties, i.e. one type of section properties).

```
type-3 property                   in a tree's pre-order trace
==============================    ===============================
    ...                           |-s3--------------------------|
    <n property="value">          | <n> .. </n> .. </p> .. </r> |
      [ descendants included ]    |-----------------------------|
    </n>
    [ siblings included ]
  </p>
  [ siblings of ancestors ]
</r>
```

In theory, a **type-3 property** can be defined to also apply to apply to
all the nodes that are subsequent to a defining node in the pre-order trace
of a tree (e.g. the current use of headings).

Note that implementations do not maintain a document as a list of nodes (i.e.
total orders). Since tree-like data structures are used which are missing some
of the edges (i.e. partial orders) there are **no outgoing border edges** which
would allow to propagate a property past the end of a type-2 scope. Because of
that, there is no path to the subsequent sibling of an ancestor, which is why
a property's defining node is not on the rooted path of an ancestor's former
subsequent sibling.

Note that, since a type-3 scope ends with the end of a tree's pre-order trace,
a type-3 scope may be referred to as being **unrestricted** in regards to a
tree's pre-order trace. After all, there are no more nodes subsequent to the
last node of a type-3 scope.
