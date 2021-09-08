
<!-- ======================================================================= -->
# well-formed documents

Since a parser is implemented to read a partial containment order from a tag
soup, an input document is initially assumed to be **well formed**. That is,
tags appear as pairs of start- and end-tags, and the scopes they define are
assumed to either be disjoint exor related.

However, since the input document can not be guaranteed to be the result of a
previous serialization (e.g. a hand-written tag soup), and not even that the
implementation used to produce the input document is without errors, a parser
must take into account that it might encounter a **malformed** document. That
is, an input document might be such that it contains start- and end-tags for
which **a matching tag is missing**.

```
      a missing start-tag          a missing end-tag
.., <a>, .., </c>, .., </a>, .., <b>, .., <d>, .., </b>, ..
```

Likewise, an implementation must take into account that an input document might
be such that the pairs of start- and end-tags define **overlapping scopes**.

```
      overlapping scopes
<a>, .., <b>, .., </a>, .., </b>
|->-a-------------->-|
         |->-b--------------->-|
```

Note that the scope of node `a` can be said to **reach into** the scope of node
`b`. Likewise, the scope of node `b` can be said to **reach out of** the scope
of node `a`. (Note the reocurring duality - i.e. matching pairs of converse
statements).

<!-- ======================================================================= -->
## xml - well-formed documents

The XML specification defines rules under which a document can be described as
**well-formed**. The rules that are relevant in the context of this discussion
can be summarized as follows:

* (R1) each start-tag `<tag>` has an end-tag `</tag>` subsequent to it
* (R2) for each end-tag there is a start-tag presequent to it
* (R3) the scope of a node that begins with the child of a parent
  must end within the parent's scope

Note that authors are advised to ensure that a document is always well-formed.
That is because implementations may react differently in response to a
**malformed** document.

<!-- ======================================================================= -->
## html - implied start- and end-tags

The HTML specification introduces the concept of "implied tags", which in
essence allows for certain tags to be missing under specific conditions.
Conforming implementations are thus required to support these cases.

<!-- ======================================================================= -->
## well-formedness

In order for a document to define an actual hierarchy of scopes, and therefore
to correspond with an actual node tree, the document's sequence of tags must
be well formed according to all of the following rules:

* (R1) each start-tag `<tag>` has an end-tag `</tag>` subsequent to it
* (R2) for each end-tag there is a start-tag presequent to it
* (R3) the scope of a node that begins with the child of a parent
  must end within the parent's scope

A document that is in conflict with any of these rules must be understood
to be **malformed**. As such, a parser may in general cancel the process of
reading it because the definition a malformed document contains is broken.

Note that rule (R3) guarantees that no scope reaches into or out of another
scope. Because of that, a conforming document defines no overlapping scopes.
As a matter of consequence, the scope of a node `n` in regards to the scope
of another node `x` can only be of the following:

* (1) disjoint - `<n> .. </n> .. <x> .. </x>`
* (2) disjoint - `<x> .. </x> .. <n> .. </n>`
* (3) a superset - `<n> .. <x> .. </x> .. </n>`
* (4) a subset - `<x> .. <n> .. </n> .. </x>`

Note that (1) is dual to (2), and (3) dual to (4).
