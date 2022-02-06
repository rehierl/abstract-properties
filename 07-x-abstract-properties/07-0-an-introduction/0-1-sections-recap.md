
# A quick recap on sections

The following introduces the concept of abstract properties as a generalization
of the concept of sections. However, before properties can be introduced, it is
essential to recall the fundamental aspects involved:

(*) A document consists of distinct nodes such that each document has a first
and a last node. As such, each document has a well defined node order (aka.
**the document order**) over its nodes. Because of that, each node has a unique
index associated with it, which is why a document can be described as an ordered
sequence of nodes.

(*) Each heading is classified as a sectioning node and is understood to declare
(aka. introduce) a new section. Because of that, a heading and its section can
be said to be associated with each other. A strong one-to-one (1:1) relationship
therefore exists between each sectioning node and the section it declares.

(S1) No node above of a heading belongs to the section it declares. That is,
if the document order is layed out vertically, in a top-to-bottom fashion.
In other words, and if the document order is layed out horizontally in a
left-to-right fashion, no node presequent to a heading in the document order
belongs to the section it declares. Note that this rule is clear since
**none-of** the corresponding nodes are nodes within the heading's section.

(S2) The nodes below-of, or subsequent-to a heading may or may not belong to
its section. Note that this rule is unclear since **some-of**, but not all of
the corresponding nodes are within the heading's section.

(S3) By default, the section of a heading includes **all-of** the nodes that
are subsequent to it. That is, if the document has no further heading. Note
that this rule is clear since all-of the corresponding nodes are included.

(*) **The scope-based perspective** of a section is such that each section has
a first and a last node, and contains every other node in between. Because of
that, the section of a heading is a substring to the document order and, as
such, consists of consecutive nodes (i.e. no gaps).

(*) **The stream-based perspective** of a section is such that a new section
object is created when reaching a sectioning node and marked as "open for
associations". In addition to that, and once an implementation has reached
past the end of a section, the corresponding section object is marked as being
"closed".

(*) A section is **considered to contain its sectioning node** since. That is
because this effectively guarantees that no section will ever be truly empty.
Furthermore, each section (as a set of nodes) is guaranteed to be distinct to
every other section since each sectioning node is defined to always declare
one section only. Based on that, a sectioning node is considered to be the
very first node within the section it declares. If need be, one can classify
each node within a section as "control nodes" or as "content nodes".
