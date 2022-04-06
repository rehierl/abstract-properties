
<!-- ======================================================================= -->
# the semantics of start- and end-tags

Questions arise about the semantics of start-tags and end-tags while parsing
the tag soup of a document. That is because start-tags and end-tags can both
be **understood to trigger events** in regards to the corresponding scope of
a node. With that in mind, the process of parsing a document can be described
as **an event-driven process**.

* (1) each **start-tag** can be understood to trigger an **enter-event**
* (2) each **end-tag** can be understood to trigger an **exit-event**

Note that all the start-tags can be understood to represent an **enter-order**
(i.e. a sequence of enter events) and all the end-tags can be understood to
represent an **exit-order** (i.e. a sequence of exit events). Combined, the
tag soup of a document can be understood to define a sequence of enter- and
exit events.

```
enter ->|-s(n)------------------------------------------------------->|-> exit
    .., | <n attribute*>, <fc>, .., </fc>, .., <lc>, .., </lc>,  </n> |, ..
 open ->|-a-substream-of-nodes--------------------------------------->|-> close
        |-ce(n)---------|-iss(n)------------------------------|-empty-|
      ->|-visit---------|<-
```

Since each node is pushed into its **start-tag**, and since the pair of tags of
a node is used to enclose all of the nodes in its scope, the start-tag of a node
can be understood to denote the **characteristic element** `ce(n)` of its scope.
Based on that, a start-tag can be understood to separate the characteristic
element (CE) of a scope from its inner subset `iss(n)`.

Since each enter-event is paired with a subsequent exit-event, the tag-based
syntax can be understood to support **a stream-based point of view**. Hence,
each pair of tags can be said to denote a sub-stream of nodes.

Note that, if all end-tags are removed from the tag soup of a document, then
the resulting sequence of **start-tags** in essence reflects the pre-order node
order of a document tree. In other words, the start-tags in the tag soup of a
document tree can be said to **appear in pre-order**.
