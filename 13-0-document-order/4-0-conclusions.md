
<!-- ======================================================================= -->
# conclusions

The following summarizes key aspects of the tag-based syntax
and essential conclusions that can be drawn from it.

<!-- ======================================================================= -->
## the tag-based syntax

```
n -|-> ns .. ls
   |-> <tag> fc .. lc </tag>
```

The tag soup of a document tree can be **formed as follows**.

- (1) inject tag-based markers
- into the unordered document tree (DTU)
- inject the start-tag of a node as its first child
- inject the end-tag of a node as its last child
- (2) form the ordered document tree (DTO)
- by embedding the document tree's child order
- (3) form the pre-order trace (PRE)
- by applying the pre-order rule
- the resulting sequence is a sequence of nodes and tags
- (4) name the tags of a node using the node's name
- (5) push each node into its start-tag
- embed the definition of each node into its start-tag
- each node is defined by the start-tag's attributes
- (6) the resulting sequence is a pure sequence of tags
- aka. the document tree's tag soup

Based on that, the **semantics** of the tags in a tag soup are as follows.

```
enter ->|-s(n)------------------------------------------------------->|-> exit
    .., | <n attribute*>, <fc>, .., </fc>, .., <lc>, .., </lc>,  </n> |, ..
 open ->|-a-substream-of-nodes--------------------------------------->|-> close
        |-ce(n)---------|-iss(n)------------------------------|-empty-|
      ->|-visit---------|<-
```

From a parser-based point of view, the tag soup of a document can be understood
to correspond with the document tree's pre-order trace - with the additional
feature that there is an end-marker for the scope of each node.

- each start-tag corresponds with the pre-order visit of a node
- each start-tag defines the beginning of the node's scope
- the attributes of each start-tag completely define a node
- each start-tag defines the absolute position of a node
- each start-tag denotes the scope's characteristic element (CE)
- each end-tag defines the end of the corresponding scope
- end-tags do not define any node - they are mere end-markers

<!-- ======================================================================= -->
## a tag soup ain't no document tree

```
.. <n> <fc> .. </fc> .. <lc> .. <l></l> </lc> </n> ..
   |-n------------------------------------------>|
       |-fc------->|    |-lc--------------->|
                                |-l-->|
```

The tag soup of a document tree does not define an actual tree. Instead, a
tag soup **defines a partial containment order**. As a matter of consequence,
hand-written documents must be well-formed

- a tag soup encodes **a hierarchy of scopes**
- a tag soup defines a containment order - not a node tree
- a tag soup embeds the document tree's pre-order node order
- the document tree's tree order is embedded as a partial suborder

Note that any edge in a document tree can be said to lead from one start-tag
to another start-tag that is subsequent to it in the document tree's tag soup.
That is because the pre-order trace of a document tree is **order preserving**.

<!-- ======================================================================= -->
## the document order is the pre-order node order

- the definition of document order
- the document order is the pre-order node order

<!-- ======================================================================= -->
## when to associate

Note that the edges defined by the pre-order rule are not embedded into the
document tree. That is, according to a document tree, a child is not presequent
to any of the subsequent siblings of its ancestors. In other words, the next
subsequent sibling of a node is not subsequent to any of its descendants.

- when to associate
- no ancestor is within the scope of a descendants
Note that, since the start-tag of a node can be understood to define a node
and also its absolute position in the document order, and since the document
order is in pre-order, no ancestor of a node is subsequent to any of its
descendants. Because of that, no ancestor can belong to any property that is
defined by any of its descendants.

<!-- ======================================================================= -->
## html elements
