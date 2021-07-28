
# A quick recap on sections

The following content will introduce generic properties as an abstraction
of the section concept. However, before these generic properties can be
introduced, it is essential to recall the fundamental aspects involved:

(*) A document consists of distinct nodes such that each document has a first
and a last node. As such, each document has a well defined order (aka. the
document order) over its nodes. Because of that, each node within a document
has a unique index associated with it, which is why a document can be described
as an ordered sequence of nodes.

(*) Each heading is classified as a sectioning node and as such said to declare
(aka. introduce) a new section. Because of that, each heading is said to be
associated with the section it declares. Likewise, each section is said to be
associated with the sectioning node by which it was introduced. Consequently,
a strong one-to-one (1:1) relationship exists between a sectioning node and its
section.

(*, S1) No node above of a heading belongs to the section it declares. That is,
if the document order is layed out vertically, in a top-to-bottom fashion. Put
differently, no node presequent to a heading belongs to the section it declares.
That is, if the document order is layed out horizontally, in a left-to-right
fashion. Note that this rule is clear since "none of" the corresponding nodes
are nodes within the heading's section.

(*, S2) The nodes below of (or subsequent-to) a heading may or may not belong
to its section. Note that this rule is unclear since "some, but not all of"
the corresponding nodes are nodes within the heading's section.

(*, S3) By default, the section of a heading includes all of the nodes that are
subsequent to it. That is, if the document has no further heading. Note that
this rule is clear since "all of" the corresponding nodes are included.

(*) The scope-based perspective of a section is such that each section has a
first and a last node, and contains every other node in between. As such, the
section of a heading is a substring to the document order.

(*) The stream-based perspective of a section is such that a new section object
is created and marked as "open for associations" as soon as the section's
sectioning node is reached. In addition to that, and once an implementation has
reached past the end of the section, the corresponding section object is marked
as being "closed".

(*) As an initial assumption, a section is considered to contain its sectioning
node and its descendant nodes since this effectively guarantees that no section
will ever be truly empty. In addition to that, each section (as a set of nodes)
is distinct to every other section. Because of that, a sectioning node always
is the very first node within the section it declares. If need be, one can
classify the nodes of a section as "control nodes" and as "content nodes".
