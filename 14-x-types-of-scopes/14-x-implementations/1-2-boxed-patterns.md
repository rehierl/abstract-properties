
<!-- ======================================================================= -->
# A pattern-based overview

The difficulty of an implementation is to map the exit-event of each scope onto
the end-tag of a surrounding container. (Recall that an end-tag may mark the
end of more than one scope).

Note that the following must be understood from the perspective of a document
tree traversal, not from the context of reading a tag-based encoding.

<!-- ======================================================================= -->
## type-0 scopes

```
|-t0-scope------|
|     node n    |
|---------------|
enter     exit-t0
```

The event-based mapping is more or less theoretical in the context of a type-0
scope. That is because both events of such a scope map onto the visit of the
corresponding defining node.

* Open the scope when entering the node's start-tag.
* Close the scope when leaving its start-tag.
* e.g. an `id` attribute

In contrary to that, the exit event of any other type of scope must be mapped
onto the type-1 exit event of a the defining node (t1), or its parent node (t2),
or the doctree's root (t3).

<!-- ======================================================================= -->
## type-1 scopes

```
|-t1-scope--------|
| n | descendants |
|-----------------|
visit       exit-t1
```

In regards to a type-1 defining node, the scope's exit event must be mapped
onto the type-1 exit event of the defining node.

* Open the scope when entering the node's start-tag.
* Close the scope when processing the node's end-tag.
* e.g. the `hidden` attribute

Note that the node's type-1 exit event is guaranteed to be triggered, if input
errors don't have to be taken into account. In regards to a type-1 property,
the scope's **parent container** is the defining node.

<!-- ======================================================================= -->
## type-2 scopes

```
|-t1-scope------------------------|
|      |-t2-scope-----------------|
| p .. | n |   data   |  content  |
|      |--------------------------|
|      visit      exit-t1  exit-t2|
|---------------------------------|
```

In regards to a type-2 defining node, the scope's exit event must be mapped
onto the type-1 exit event of the defining node's parent.

* Open the scope when entering the node's start-tag.
* Close the scope when processing the parent's end-tag.
* e.g. heading-based section properties

Note that a type-2 defining node is in general neither required to have
a descendant, nor a subsequent sibling. That is, the "data" and "content"
areas in the property's scope may both be empty.

Note that a type-2 defining node must be treated as a type-1 defining node,
if the defining node is the document tree's root node.

<!-- ======================================================================= -->
## type-3 scopes

```
|-t1-scope-----------------------------------|
|      |-t3-scope----------------------------|
| r .. | n |  data  |  content  | ???        |
|      |-------------------------------------|
|      visit    exit-t1     exit-t2   exit-t3|
|--------------------------------------------|
```

Similar as above, and in regards to a type-3 defining node, the scope's exit
event must be mapped onto the type-1 exit event of the tree's root.

* Open the scope when entering the node's start-tag.
* Close the scope when processing the root's end-tag.
* e.g. unclear use - kept for the sake of argument ...

Note that a type-3 defining node must be treated as a type-2 defining node,
if the defining node is a child to the document tree's root node. Similar to
that, it must be treated as a type-1 defining node, if the defining node is
the document tree's root node.
