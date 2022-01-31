
<!-- ======================================================================= -->
# An initial terminology

Since there are many questions that need to be answered, the definitions below
need to be understood to introduce a general, but still rough terminology. That
is, the exact meaning of the following definitions will be subject to change.

<!-- ======================================================================= -->
## basic terms

The content that is associated with a heading is referred to as its **section**.
Based on that, each heading is understood to **introduce**, or to **declare**
a new section. Furthermore, a heading may in general be described/classified
as a **sectioning node**.

Since a heading always declares a new section, each heading is said to be
accompanied by the section it declares. That is, even if its section has no
content (i.e. it appears to be empty), a heading and its section are both
said to be **associated with**, or to be **related with** each other.

- Each sectioning node declares a new section.
- Each section has its own sectioning node.
- One does not exist without the other.

Note that since the relationship between a heading and its section is a strict
**1:1 relationship**, a heading may be identified by its section and vice
versa. Example fragments will therefore in general use the descendants of a
heading, usually its title (T), to identify the section it declares. That is,
the heading in the following fragment is said to declare section T.

```
 <h> T </h>
|------------|
| section T  |
|------------|
```

Since each section must be declared before it can exist (recall statement S1),
one can conclude that there is a structural relationship between a heading and
its section: That is, a heading always appears **above** the very first node
in its section. Because of that, the placement of a heading is significant.

**The nodes of a section** are said to be **associated** with it, and also
with the section's heading. As such, the nodes of a section are said to be
**elements in** and also to be located **inside of** all the sections to
which they belong. Based on that, a section can be said to **contain** all
the nodes in it.

<!-- ======================================================================= -->
## context, scope

```
       |  document  |
-------|------------|---------
       | ...        |
 above | A          | context
-------|------------|---------
       | <h> T </h> | ?
-------|------------|---------
 below | B          | scope
       | ...        | first-to-last
       | C          |
       |------------|---------
       | ...        |
```

All of the the nodes that are above a heading, and which may have some effect
on it and its section, can be understood to contribute to the **context** of
a heading and the nodes in its section.

All of the nodes that are below a heading, and that can be understood to be
inside of a heading's section can be said to be inside of the **scope** of a
heading and its section. As such, these nodes can be referred to as the
**content nodes** of a heading and its section. That is, the scope of a section
begins with its first and ends with its last content node. And since a section
consists of consecutive nodes (i.e. no gaps), the scope of a section can be
described as **continuous** (note - in the sense of "consists of consecutive
nodes", not in the sense of "infinite").

As a matter of simplification, a heading and its descendants in the document
tree will be treated as being part of the heading's section. That is, these
nodes will initially be assumed to be nodes in the heading's section and
therefore also within the scope of a heading. At this point, this assumption
is no strict definition, which is why implementations may treat these nodes
differently (e.g. as bridges between sections).

Note that, from a theoretical point of view, counting headings towards the
sections they declares effectively guarantees that no section will ever be
empty. Furthermore, and since each sectioning node always declares one section
only, all the sections in a document are guaranteed to be distinct from one
another (in the sense of distinct sets of nodes). That is because they are
then guaranteed to always differ at least in their sectioning nodes.

```
    |-section---------------|
... | <h> data </h> content | ...
    |-----------------------|
```

In order to distinguish a heading from its content nodes, headings themselves
may be referred to as **control nodes**. In addition to that, the descendants
of a heading may be referred to as **data nodes** since these are in general
used to define certain properties of a section (e.g. a title).

Note that the end-tag of a heading can be understood to separate the descriptive
data of a heading (i.e. the descendants of a heading) from its actual content.
Hence, one can distinguish between the data nodes and the actual content nodes
of a section.

<!-- ======================================================================= -->
## empty sections

At some point a clear description of the document order is required since
"first node" and "last node" would otherwise be without a proper definition.
That is, one must have the means to uniquely identify the first node and the
last node of a section and also all the other nodes in between.

In order to support empty sections, the strict definition of a section's scope
will have to be independent of a section's first and its last node. Requiring
these nodes to exist would otherwise disallow empty sections (i.e. sections
with no content nodes), which is why one would then have to define what
"meaningful content" is. On top of that, and due to possible input errors,
one can simply not guarantee that a section is always non-empty.
