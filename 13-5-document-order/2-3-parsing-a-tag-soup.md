
<!-- ======================================================================= -->
# a general approach to parse a tag soup

Note that the following exemplifies how a simple stack-based parser may react
in response to a malformed input document.

Despite all the rules and regulations, implementors of parsers must still take
into account that the core issue remains as is: Prior to parsing a tag soup to
the very end, an input document can simply not be guaranteed to be well formed.

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
       ^ cursor
```

At the very beginning of a document a parser can be understood to initialize
a stack of current nodes, which effectively represents the rooted path of the
current node. The root of the document tree will be located at the very bottom
of that stack, and the current node at the very top.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
      |-r-^ cursor
```

Since each start-tag is by definition understood to define the CE of a scope,
and since `<r>` is the very first start-tag of the current sequence of tags,
a parser will assume that start-tag to define the root of the document tree.
Because of that, a parser will create a node object and push it onto the stack.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag is encountered before the very first start-tag.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r, a)
          |-a-^ cursor
```

Since the same applies when reaching start-tag `<a>`, a parser will create a
node object for `a` and push it onto the stack. However, since the stack is
non-empty, the node on the top of the stack (i.e. `r`) will be assumed to be
the parent of `a`. Because of that, node `r` will be set as the parent of
node `a`.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r, a, b)
              |-b-^ cursor
```

For reasons that should be obvious, the same applies when reaching start-tag
`<b>`. That is, `b` will be created, pushed onto the stack, and set as the
next child of `a`.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
           |-a-------|^ cursor
              |-b-|
```

Upon reaching end-tag `</a>`, the parser will search its stack for node `a`,
which it will find and thus determine that the scope of that node has ended.

However, since `a` is not the topmost element (i.e. the end-tag `</b>` appears
to be missing) on the parser's stack, the parser can also assume that scope
`s(b)` must have ended as well. After all, the expectation is such that scopes
do not overlap each other. Because of that, the parser can remove all the nodes
from its stack until the node that matches the current end tag `</a>` has been
removed.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag does not match the topmost node.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
                      |-?-|^ cursor
```

Upon reaching end-tag `</b>`, an implementation will once again search its
stack for a matching node. In contrary to before, no matching start-tag
seems to exist, which is why the end-tag may be dismissed.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag appears without a matching start-tag.

Note that, even though the start-tag does exist, the parser will still
classify the seemingly missing start-tag as an input error. The difference
is that the reason for the document's malformedness will be mis-classified
(i.e. **a false negative**). However, knowing that a negative case may be
the cause of overlapping scopes allows an implementation to verify if a
start-tag was indeed missing, which is why an implementation can in general
detect and distinguish between both cases.

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
       |-r---------------------|^ cursor
```

Finally, upon reaching end-tag `</r>`, a matching node can be found as a
node within the parser's stack. Because of that, the stack will be cleared,
which effectively states that the document has been completely processed.

Note that a strict implementation may reject an input document as being
**malformed**, if the last node has been removed from the stack of nodes,
and if the end of the document has still not yet been reached.
