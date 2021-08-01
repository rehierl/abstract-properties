
<!-- ======================================================================= -->
# The all-of, none-of and some-of quantifiers

```
|-(C)ontent-----------|
| ...                 |
|     |-(S)cope-|     |
|     |   ???   |     |
|     |---------|     |
|                 ... |
|---------------------|
```

In the end, developers will want to make use of the relationships between the
nodes of a document and the sections it contains.

For example, developers of web browsers and developers of editing software will
want to fold and unfold the contents of a section in order to limit the amount
of information that is being displayed. In general, these kinds of operations
are implemented based on hiding and re-displaying the nodes within a section.

At the very core of any operation is however the ability to reliably determine
if a given node is within a particular section or not. Because of that, a clear
definition of which nodes are affected by a sectioning node must be provided.

Once such definitions are available, an implementation can then determine all
the nodes within a section and execute some operation on them. Based on that,
an implementation can in theory be understood to first preselect all the nodes
that will be affected, and then to execute the operation on that group of nodes.

Note that such a group of nodes will in general be referred to as the **scope**
of an operation. Similar to that, one can speak of "the scope of a (generic)
property", or of "the section of a heading". That is, the terms "scope" and
"section" can both be understood to denote some "area of effect (aoe)" and
can as such be understood to refer to all of the nodes within that group.

Critical to the definition of an operation is therefore a clear and unambiguous
definition of its scope. After all, an operation is in general required to have
predictable results. That is, an operation is expected to produce results which
can be relied upon - and based on that, results that can be taken advantage of.

In most of the cases an operation is not intended to affect all of the nodes
within a document (i.e. **all-of**). Similar to that, an operation that does
not affect any node at all, is of not much use (i.e. **none-of**), since such
an operation would then have no effect at all. Because of that, an operation
will in general have an effect on "some, but not all" of the nodes within a
document (i.e. **some-of**).

Obviously, the all-of and none-of quantifiers are easy to define in the context
of a well known set of nodes, such as the nodes of a document. That is because
neither the document's structure, nor its contents are relevant to these
quantifiers: It is "either all in, ex-or none at all".

It is just as obvious that each operation must have some well known point of
origin. After all, if an operation has to be performed, it first needs to be
declared as an existing "thing" within a given context (e.g. by the node of a
document a document). One can therefore assume that the scope of an operation
always has a well known starting point, which leaves one remaining question:

At what point does the scope of an operation end, assumed that the operation
is not supposed to affect all of the other nodes?

Based on that, the difficult part is on providing unambiguous defintions for
the some-of quantifier since it requires additional bits of information that
make it clear which nodes to include, and which ones to ignore. But how does
one define "include these, but not the others", based on an abstract concept
of "a document" that is purely theoretical in the context of a definition?

The only means a definition has in that regards are the **formal rules** any
document is expected to follow. Because of that, all definitions must be based
upon such rules. These rules must therefore be known to those who develop the
defitions and known to those who use them. As such, these formal rules can be
understood **as a language that is used to communicate definitions**.
