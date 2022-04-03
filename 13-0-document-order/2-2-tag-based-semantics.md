
<!-- ======================================================================= -->
# the semantics of start- and end-tags

When trying to parse the tag soup of a document, questions arise about the
semantics of start- and end-tags. That is because, while parsing a tag soup,
both kinds of tags can be understood to trigger events with regards to the
scopes of the corresponding scopes. Based on that point of view, the process
of parsing a document can be described as **an event-driven process**.

* (1) a **start-tag** can be said to trigger an **enter-event**
* (2) an **end-tag** can be said to trigger an **exit-event**

Note that all the start-tags combined can be said to represent an **enter-order**
(i.e. a sequence of enter events) and all the end-tags an **exit-order** (i.e.
a sequence of exit events). Combined, the tag soup of a document can be
understood to define a sequence of enter- and exit events.

```
enter ->|-s(n)------------------------------------------------------->|-> exit
    .., | <n attribute*>, <fc>, .., </fc>, .., <lc>, .., </lc>,  </n> |, ..
 open ->|-a-substream-of-nodes--------------------------------------->|-> close
        |-ce(n)---------|-iss(n)------------------------------|-empty-|
      ->|-visit---------|<-
```

Note that, since each enter-event is paired with a subsequent exit-event, the
tag-based syntax can be understood to support **a stream-based point of view**.
Hence, each pair of tags can be said to denote a sub-stream of nodes.
