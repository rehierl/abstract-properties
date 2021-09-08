
<!-- ======================================================================= -->
# well-formed documents

Since a parser is implemented to read a partial containment order from a tag
soup, an input document is initially assumed to be **well formed**. That is,
tags appear as pairs of start-tags and end-tags, and the scopes they define
are either disjoint exor related.

However, since the input document can not be guaranteed to be the result of a
previous serialization (e.g. a hand-written tag soup), and not even that the
implementation used to produce the input document is without errors, a parser
must take into account that it might encounter a **malformed** document. That
is, an input document might be such it contains start- and end-tags for which
**a matching tag is missing**.

```
      a missing start-tag          a missing end-tag
.., <a>, .., </c>, .., </a>, .., <b>, .., <d>, .., </b>, ..
```

Likewise, a parser implementation must take into account that an input document
might be such that the pairs of start- and end-tags define **overlapping scopes**.

```
      overlapping scopes
<a>, .., <b>, .., </a>, .., </b>
|->-a-------------->-|
         |->-b--------------->-|
```

Note that the scope of node `a` can be said to **overlap into** node `b`.
Likewise, the scope of node `b` can be said to **overlap out of** node `a`.

<!-- ======================================================================= -->
## xml - well-formed documents

The XML specification defines rules under which a document can be described
as **well-formed**. The rules that are relevant in the context of this
discussion can be summarized as follows:

* each start-tag `<tag>` has an end-tag `</tag>` subsequent to it
* for each end-tag there is a start-tag presequent to it
* the scope of a node that begins with as the child of a parent must end as such

Note that authors are advised to ensure that a document is always well-formed.
That is because implementations may react differently in response to a
**malformed** document.

<!-- ======================================================================= -->
## html - implied start- and end-tags

The HTML specification introduces the concept of "implied tags", which in
essence allows for certain tags to be missing under specific conditions.
Conforming implementations are therefore required to support these cases.
