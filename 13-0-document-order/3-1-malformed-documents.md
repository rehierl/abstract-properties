
<!-- ======================================================================= -->
# malformed document

Despite any existing rules and regulations, implementors of parsers must always
take into account that the core issue remains as is: Prior to actually parsing
the tag soup of a document to the very end, an input document can not be
determined to be well formed. However, as soon as a tag soup can be determined
to not be well-formed, implementors have to decide what to do with such a
document: Ignore it or return some best-effort result?

The following exemplifies **a simple stack-based approach** that can be used
to detect the malformedness of an input document. In addition to that, the
following describes how an implementation could continue to read despite the
input errors that were detected. The latter of which can be summaries as
follows:

* (1) Close the scope of a start-tag with the end-tag of start-tag's parent,
  if there is no subsequent end-tag within the scope of the start-tag's parent.
* (2) Ignore an end-tag, if there is no presequent start-tag within the scope
  of the end-tag's parent.

<!-- ======================================================================= -->
## the basic approach

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
      ^ cursor                          (bottom -> top)
```

At the very beginning of a document a parser can be understood to initialize
a stack of current nodes, which will represent the rooted path of the current
node (aka. **the current rooted path**): The root of the document tree will
be located at the stack's very bottom (left-most, first node), and the current
node at the stack's very top (right-most, last node).

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
      |-r-^ cursor
```

Since each start-tag is by definition understood to define the CE of a scope,
and since `<r>` is the very first start-tag of the current sequence, a parser
will assume the start-tag to define the docment's root node. Because of that,
a parser will create a node object and push it onto the stack, while saving
that node object as the starting point (i.e. the root).

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
be created, pushed onto the stack, and set as the first/next child of `a`.

<!-- ======================================================================= -->
## a missing end-tag

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
           |-a--------|^ cursor
               |-b---------| overlapping scopes
               |-b-| resulting scope of node b
```

Upon reaching end-tag `</a>`, the parser will search its stack for node `a`,
which it will find and thus determine that its scope has ended.

However, since `a` is not the stack's topmost node (i.e. end-tag `</b>` is
missing), the parser can conclude that scope `s(b)` must have ended as well.
After all, a scope can not reach out of the scope of another node (i.e. the
DI-RE case). Because of that, the parser may choose to remove all of the
nodes from the top of its stack until node `a` has been removed.

Note that, removing all the nodes from a current stack for which no end-tag
was encountered, can be understood to implement "implied/assumed end-tags".
That is because an implementation would in essence act as if it had
encountered these missing tags in the appropriate order.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag does not match the stack's topmost node.

<!-- ======================================================================= -->
## a missing start-tag

```
tags - <r> <a> <b> </a> </b> </r>        stack - (r)
                       |-?-|^ cursor
```

Upon reaching end-tag `</b>`, an implementation will once again search its
stack for a matching node. In contrary to before, a parser may determine
that no matching start-tag seems to exist, which is why a parser may choose
to ignore that end-tag.

Note that a strict implementation may reject an input document as being
**malformed**, if an end-tag appears without a matching start-tag.

<!-- ======================================================================= -->
## overlapping scopes

Even though the start-tag does exist, the parser will initially classify the
seemingly missing start-tag as an input error. Because of that, the reason for
the document's malformedness will be mis-classified (i.e. a negative but for
the wrong reason).

However, knowing that a seemingly missing start-tag may be the cause of
overlapping scopes still allows an implementation to verify if a start-tag
was indeed missing. After all, there must have been a prior case of a missing
start-tag. That is, an implementation can in general detect and distinguish
between both cases - i.e. overlapping or indeed missing.

<!-- ======================================================================= -->
## finish the parsing process

```
tags - <r> <a> <b> </a> </b> </r>        stack - ()
       |-r----------------------|^ cursor
```

Finally, upon reaching end-tag `</r>`, a matching node can be found in the
parser's stack. Because of that, the stack will be cleared, which effectively
allows to state that the document has been processed completely.

Note that a strict implementation may reject an input document as being
**malformed**, if all nodes are removed from the stack while the last
input tag has not yet been processed (i.e. a forest of trees).

Note that a strict implementation may reject an input document as being
**malformed**, if the stack still has nodes once the implementation has
processed all of the input tags.
