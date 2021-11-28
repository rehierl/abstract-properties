
<!-- ======================================================================= -->
# parsing a malformed document

Note that the following exemplifies how a simple stack-based parser may detect
the malformedness of an input document.

Despite all the rules and regulations, implementors of parsers must still take
into account that the core issue remains: Prior to parsing a tag soup to the
very end, an input document can not be determined to be well formed.

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
      ^ cursor                         (bottom -> top)
```

At the very beginning of a document a parser can be understood to initialize
a stack of current nodes, which effectively represents the rooted path of the
current node (aka. **the current rooted path**): The root of the document tree
will be located at the stack's very bottom, and the current node at the stack's
very top.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
      |-r-^ cursor
```

Since each start-tag is by definition understood to define the CE of a scope,
and since `<r>` is the very first start-tag of the current tag sequence, a
parser will assume the start-tag to define the docment's root node. Because
of that, a parser will create a node object and push it onto the stack.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag is encountered before the very first start-tag.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r, a)
          |-a-^ cursor
```

Since the same applies when reaching start-tag `<a>`, a parser will create a
node object for `a` and push it onto the stack. However, since the stack is
non-empty, the node on the top of the stack (i.e. `r`) is understood as the
parent of `a`. Because of that, `r` will be set as the parent of `a`.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r, a, b)
              |-b-^ cursor
```

Obviously, the same applies when reaching start-tag `<b>`. That is, `b` will
be created, pushed onto the stack, and set as the next child of `a`.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
           |-a--------|^ cursor
               |-b---------| overlapping scopes
               |-b-| resulting scope of node b
```

Upon reaching end-tag `</a>`, the parser will search its stack for node `a`,
which it will find and thus determine that its scope has ended.

However, since `a` is not the stack's topmost element (i.e. end-tag `</b>` is
missing), the parser may conclude that scope `s(b)` must have ended as well.
After all, a scope can not be allowed to reach out of the scope of another
node (i.e. the DI-RE case). Because of that, the parser may choose to remove
all of the nodes from the top of its stack until node `a` has been removed.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag does not match the stack's topmost node.

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
                       |-?-|^ cursor
```

Upon reaching end-tag `</b>`, an implementation will once again search its
stack for a matching node. In contrary to before, a parser may determine that
no matching start-tag seems to exist, which is why a parser may choose to
ignore the end-tag.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag appears without a matching start-tag.

Note that, even though the start-tag does exist, the parser will classify
the seemingly missing start-tag as an input error. The difference is that the
reason for the document's malformedness will be mis-classified (i.e. a false
negative but for the wrong reason). However, knowing that a negative case may
be the cause of overlapping scopes still allows an implementation to verify
if a start-tag was indeed missing, which is why an implementation can in
general detect and distinguish between both cases.

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
       |-r----------------------|^ cursor
```

Finally, upon reaching end-tag `</r>`, a matching node can be found in the
parser's stack. Because of that, the stack will be cleared, which effectively
allows to state that the document has been processed completely.

Note that a strict implementation may reject an input document as being
**malformed**, if the last node has been removed from the stack, and if
the end of the document has not yet been reached.
