
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
of information that is being displayed. In general, these kind of operations
are implemented based on hiding and re-displaying the nodes within a section.

At the very core of any operation is however the ability to reliably determine
if a given node is within a particular section or not. Because of that, a clear
definition of which nodes are affected by a sectioning node must be provided.

Once such definitions are available, an implementation can determine all of
the nodes within a section and execute some operation on them. Based on that,
an implementation can in theory be understood to first preselect all the nodes
that will be affected, and then to execute the operation on that group of nodes.

Note that such a group of nodes will in general be referred to as the **scope**
of an operation. Similar to that, one can speak of "the scope of an abstract
property", or of "the section of a heading". That is, the terms "scope" and
"section" can both be understood to denote some **area of effect (aoe)** and
can as such be understood to refer to all of the nodes within that group.

Critical to the definition of an operation is therefore a clear and unambiguous
definition of its scope. After all, an operation is in general required to have
predictable results. That is, implementations are expected to produce results
which can be relied upon - results that can be taken advantage of.

<!-- ======================================================================= -->

```
|- document/visit order -- none-/all-/some-of --------->|
```

In most cases an operation is not intended to affect all of the nodes within a
document (**all-of**). Similar to that, an operation that does not affect any
node at all, is of not much use (**none-of**), since such an operation would
then have no effect at all. Because of that, an operation will in general have
an effect on "some, but not all" of the nodes in a given context (**some-of**).

Obviously, the all-of and none-of quantifiers are easy to define in the context
of a well known set of nodes, such as the nodes of a document. That is because
neither the document's structure, nor its contents are relevant to them: It is
"either all included, ex-or none at all".

<!-- ======================================================================= -->

```
|- document/visit order -- d -------------------------->|
|- d is unknown ---------->|- d is known -------------->|
                           |- all-of ------------------>|
```

The difficulty is therefore to provide a clear definition of the some-of
quantifier. However, one can assume that there is a known total order defined
over the nodes of a document. That is because all implementations must visit
the nodes of a document in the exact same order (aka. **the processing order**).
One would otherwise end up with implementations that return different results
for the same document. Needless to state, that kind of outcome must be avoided.

It is just as obvious that each operation must have some well known point of
origin. After all, if an operation has to be performed, it first needs to be
declared as an existing "thing" (e.g. by some node `d`). One can therefore
assume that the scope of an operation always has a well known starting point,
which will be referred to as its **defining node**.

Based on that one can conclude, that the scope of an operation can not include
any of the nodes that were visited before the operation's defining nodes was
visited (i.e. none-of those nodes that are presequent to the defining node).
Because of that, the scope of an operation can only be a subset of those nodes
that are subsequent to the operation's defining node.

Note that this observation has no effect on the none-of quantifier. However,
in regards to the all-of and some-of quantifiers, this can be understood as
a restriction that results from having to visit the nodes of a document in a
particular order.

```
|- document/visit order -- d -------------------------->|
|- none-of --------------->|- all-of ------------------>|
|- some-of -------------------------------------------->|
```

Note that the above already effectively describes how a some-of quantifier
can be defined in terms of a none-of and an all-of quantifier.

<!-- ======================================================================= -->

```
|- document/visit order -- d ----------- l ------------>|
|- none-of --------------->|- all-of --->|- none-of --->|
                           |- some-of ----------------->|
```

If neither none-of nor all-of the nodes that can possibly be affected by an
operation are to be included within a scope, one can assume that the scope
may only extend over the first few nodes that are subsequent to `d`. That is,
the operation's scope can be assumed to begin with the defining node up to
and including to some last node `l`. Based on that, a scope can be assumed
to contain all-of the nodes within a certain range `[d,l]`, but none-of the
nodes after that.

This leaves one remaining question unanswered: At what point does the scope
of an operation end, assumed that the operation is not supposed to affect
all-of the nodes that are subsequent to a defining node?

Due to the above, the difficult part is on providing unambiguous defintions
for the some-of quantifier since it requires additional bits of information
that make it clear which nodes to include, and which ones to ignore. But how
does one reliably define "include these, but not the others", based on an
abstract concept of "a document" that is purely theoretical in the context
of a definition/specification?

The only means a definition has in that regards are the **formal rules** any
document is expected to follow. Because of that, all definitions must be based
upon such rules. These rules must therefore be known to those who develop a
design and to those who use it. These formal rules can therefore be described
**as a language that is used to communicate a design** and its definitions.
