
<!-- ======================================================================= -->
# A pattern-based point of view

The following content is intended to provide visualizations of patterns that
could be used in the context of discussions.

Note that the defining nodes of type-2 and type-3 properties must have parent
nodes. The scopes of these properties could otherwise not be closed. Because
of that, a root node can not be used as the defining node of such a property.

<!-- ======================================================================= -->
## box-based visualizations

```
<r>                     <n>           </n>         </p>    </r>
-|-----------------------|--------------|------------|-------|-
 r × .. p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) × ..
-----------------------|----------------|------------|---------
                       |<- traceU(n)  ->|            |
                       |<- prefix     ->|<- suffix ->|
                       |<- traceO(n)               ->|
```

The difficulty of an implementation is to map each exit-event of a document
traversal onto the exit-event of one or more scopes. (Note that an end-tag
may mark the end of more than one scope).

Recall that a node which defines a property, is referred to as the property's
defining node. In regards to the property's type/scope, a defining node may be
referred to as **a type-x (defining) node**. That is, a type-x node is said to
define a type-x property.

<!-- ======================================================================= -->
## type-0 properties

```
|-t0-scope------|
|     node n    |
|---------------|
enter   t0-exit-n
```

The event-based mapping is more or less theoretical in the context of a type-0
node. That is because both events of such a scope map onto the visit event of
its defining node.

* Open the scope while visiting the defining node.
* Close the scope when leaving the node's visit event.
* Close the scope when the node's type-0 exit event is triggered.
* e.g. an `id` attribute

In contrary to that, the exit event of any other type of scope must be mapped
onto the type-1 exit event of a node.

<!-- ======================================================================= -->
## type-1 properties

```
|-t1-scope--------|
| n | descendants |
|-----------------|
enter     t1-exit-n
```

In regards to a type-1 defining node, the scope's exit event must be mapped
onto the type-1 exit event of the defining node.

* Open the scope while visiting the defining node.
* Close the scope just after exiting the node's last descendant.
* Close the scope when the node's type-1 exit event is triggered.
* e.g. the `hidden` attribute

Note that the node's type-1 exit event is guaranteed to be executed, if input
errors don't have to be taken into account. Also, the node that is responsible
to close a property's scope will be referred to as the property's **parent
container**. In regards to a type-1 property, that parent container is the
defining node.

<!-- ======================================================================= -->
## type-2 properties

```
|-t1-scope-------------------------|
|      |-t2-scope-----------------||
| p .. | n |   data   |  content  ||
|      |--------------------------||
|      enter  t1-exit-n   t1-exit-p|
|----------------------------------|
```

In regards to a type-2 defining node, the scope's exit event must be mapped
onto the type-1 exit event of the defining node's parent.

* Open the scope while visiting the defining node.
* Close the scope just after t1-exiting the last subsequent sibling.
* Close the scope when the type-1 exit event of parent `p` is triggered.
* e.g. heading-based section properties

Note that a type-2 defining node **must have a parent node**. That is, using
a tree's root to define a type-2 property is an input error. The root of a
tree can therefore not be a type-2 defining node.

Despite that, a type-2 defining node is neither strictly required to have a
descendant, nor any subsequent sibling. That is, the "data" and "content"
areas in the property's scope may be empty.

Note that, provided there are no input errors, both exit events (i.e. the
type-1 exit event of node `n` and the type-1 exit event of node `p`) are
triggered as separate events since nodes `n` and `p` are distinct nodes.

<!-- ======================================================================= -->
## type-3 properties

```
|-t1-scope-------------------------------|
|      |-t3-scope-----------------------||
| r .. | n |  data  |  content  |  ???  ||
|      |--------------------------------||
|      enter   exit-n      exit-p  exit-r|
|----------------------------------------|
```

Similar as above, and in regards to a type-3 defining node, the scope's exit
event must be mapped onto the type-1 exit event of the tree's root.

* Open the scope while visiting the defining node.
* Close the scope when the type-1 exit event of root `r` is triggered.
* e.g. unclear use - kept for the sake of argument ...

Note that, if a type-3 defining node is a child to the tree's root, then the
type-1 exit event of the node's parent and the type-1 exit event of the tree's
root are identical (i.e. `(exit-p == exit-r)` may be true). That is because
both nodes are in such a case identical. Other than that, and provided there
are no input errors, all type-1 exit events are guaranteed to be triggered.
