
# An introduction to generic properties

<!-- ======================================================================= -->
## why "generic properties"?

Describing the following concept of properties as "generic" is intended to
reduce confusion. That is because the description of a characteristic as a
"property" has, depending on a given context, different meaning.

For example, the overall structure of the connections between vertices (e.g. as
acyclic) can be described as a property of the corresponding relation (i.e. a
graph property). Likewise, the concrete feature or characteristic of an object
(e.g. its weight) is in general also described as a "property".

In contrary to that, the use of the term "property" as described below abstracts
the general process of marking all the elements (e.g. with some color) that will
be affected by an operation. As such, these kind of properties can be understood
as being purely abstract in nature.

However, and since these properties can be understood to correspond with scopes,
they can in general be used to define concrete object properties and the scopes
of operations. Based on that, one could also speak of **generic scopes** or of
**types of scopes** rather than of "generic properties".

<!-- ======================================================================= -->
## scopes of operations

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
if a given node is within a specific section. Because of that, clear definitions
of which nodes are affected by some sectioning node must be provided.

Once such definitions are available, an implementation can then determine all
the nodes within a section and execute some operation on them. Based on that,
an implementation can in theory be understood to first preselect all the nodes
that will be affected, and then to execute the operation on that group of nodes.

Note that such a group of nodes will in general be referred to as the **scope**
of an operation. Similar to that, one can speak of "the scope of a property",
or of "the section of a heading". That is, the terms "scope" and "section" can
both be understood to denote some "area of effect (aoe)" and can as such be
understood to refer to all of those nodes that are whithin that group.

<!-- ======================================================================= -->
## the all-of, none-of, some-of quantifiers

Critical to the definition of an operation is therefore a clear and unambiguous
definition of its scope. After all, an operation is in general required to have
predictable results. That is, an operation is expected to produce results that
can be relied upon, results that can be taken advantage of.

In most of the cases an operation is not intended to affect all of the nodes
within a document (i.e. **all-of**). Similar to that, an operation that does
not affect any node at all, is of not much use (i.e. **none-of**), since such
an operation would then have no effect at all. Because of that, an operation
will in general affect "some, but not all" of the nodes within a document (i.e.
**some-of**).

Obviously, the all-of and none-of quantifiers are easy to define in the context
of a well known set of nodes, such as the set of nodes of a document. That is
because neither the document's structure, nor its contents are relevant to these
quantifiers: It is "either all in ex-or none at all".

It is just as obvious that each operation must have some well known point of
origin. After all, if an operation has to be performed, it first needs to be
declared within a given context (such as a document). One can therefore assume
that the scope of each operation has a well known starting point, which leaves
only one question open: At which point does a scope end that is not supposed
to include all of the other nodes?

Based on that, the difficult part is on providing unambiguous defintions for
the some-of quantifier since it relies upon additional bits of information. But
how does one define which nodes to include, and which ones to ignore, based on
an abstract concept of "a document" that is purely theoretical in the context
of a definition?

The only means a definition has in that regards are the **formal rules** any
document is expected/required to follow. Because of that, all definitions must
be based upon these rules, which is why these rules must be known to those who
make the defitions and to those who use them. As such, these formal rules can
be understood **as a language that is used to communicate definitions**.
