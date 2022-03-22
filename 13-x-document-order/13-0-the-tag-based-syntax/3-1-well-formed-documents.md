
<!-- ======================================================================= -->
# well-formed documents

An input document is initially assumed to be **well formed**. That is, tags
are assumed to appear as pairs of start- and end-tags, and the scopes they
define are assumed to either be disjoint ex-or related.

```
    a missing start-tag          a missing end-tag
    i.e. a missing <c> tag       i.e. a missing </d> tag
.., <a>, .., </c>, .., </a>, .., <b>, .., <d>, .., </b>, ..
```

However, since an input document can not be guaranteed to be the result of a
previous serialization (e.g. a hand-written tag soup), and not even that the
implementation used to produce an input document is without errors, a parser
must take into account that it might encounter a **malformed** document. That
is, an input document might be such that it contains start- and end-tags for
which there is **no matching tag**.

```
      overlapping scopes
<a>, .., <b>, .., </a>, .., </b>
|>-a---------------->|
         |>-b----------------->|
```

Likewise, an implementation must take into account that an input document might
be such that the pairs of start- and end-tags define **overlapping scopes**.

Note that the scope of node `a` can be said to **reach into** the scope of node
`b`. Likewise, the scope of node `b` can be said to **reach out of** the scope
of node `a`.

<!-- ======================================================================= -->
## xml - well-formed documents

The XML specification defines rules under which a document can be described as
**well-formed**. The rules that are relevant in the context of this discussion
can be summarized as follows:

* (R1) each start-tag `<tag>` has an end-tag `</tag>` subsequent to it
* (R2) for each end-tag there is a start-tag presequent to it
* (R3) a start-tag and its end-tag must have the same parent

Note that authors must ensure that a document is well-formed. That is because
implementations might produce different results when parsing a non-conformant
document.

<!-- ======================================================================= -->
## html - implied start- and end-tags

The HTML specification introduces the concept of "implied tags", which allows
for certain tags to be missing under certain conditions. Implementations that
conform to HTML's rules are required to support these special cases.

<!-- ======================================================================= -->
## (strict) well-formedness

In order for a document to define an actual hierarchy of scopes, and therefore
to correspond with an actual document tree, the document's sequence of tags
must be **well-formed** by following the following rules. A document that is
in conflict with any of these rules is understood to be **malformed**.

* (R1) each start-tag `<tag>` has an end-tag `</tag>` subsequent to it
* (R2) for each end-tag there is a start-tag presequent to it
* (R3) a start-tag and its end-tag must have the same parent

Note that a parser may in principle cancel the process of processing a
malformed input document. That is because the definition of a document tree,
as defined by a malformed tag soup, is broken.

Note that rule (R3) guarantees that no scope reaches into or out of another
scope. Because of that, a conforming document can not define overlapping
scopes. As a matter of consequence, the scope of a node `n` in regards to
the scope of another node `x` can only be one of the following:

* (1) disjoint - `<n> .. </n> .. <x> .. </x>`
* (2) disjoint - `<x> .. </x> .. <n> .. </n>`
* (3) a superset - `<n> .. <x> .. </x> .. </n>`
* (4) a subset - `<x> .. <n> .. </n> .. </x>`

Note that (1) is dual to (2), and that (3) is dual to (4).
