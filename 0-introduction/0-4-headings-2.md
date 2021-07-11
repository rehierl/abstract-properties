
<!-- ======================================================================= -->
# An introduction to headings and sections (2)

<!-- ======================================================================= -->
## special case: one heading only

In regards to statement S2 one special case can be pointed out:

If a document has one and only one heading, then the section of that heading
is in general understood to contain all of the nodes that are below the
section's heading. That is because there is no further explicit definition
embedded into the document that could force the section to end prematurely.

- (S3) By default, the section of a heading includes all of the nodes
  that are below/beneath the section's heading.

S3 can therefore be understood to clarify S2 in that particular case.
In addition to that, S3 can be said to define **the default scope**
of a section.

Note that S3 is just as clear as S1 since all-of the corresponding nodes
are by default included. Because of that, the heading's section seems to
be unrestricted (i.e. no "if", no "but" and no "maybe").

Note that the above/below node order has, at this point, no strict formal
foundation/definition. Such a definition is however still required since
implementations need to be able to determine if a node is below/beneath
a particular heading.

<!-- ======================================================================= -->
## special case: no heading at all

The following question can be asked in regards to S1: To which section do the
nodes above the very first heading of a document belong? Put differently, to
which section do the nodes of a document belong, if there is no heading at all?

TODO
- introduce the universal section
- different types of sectioning nodes
