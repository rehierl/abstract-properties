
<!-- ======================================================================= -->
# An introduction to headings and sections (2)

<!-- ======================================================================= -->
## special case: one heading only

In regards to statement S2 one special case can be highlighted:

If a document has one and only one heading, then the section of that heading is
in general understood to contain all of the nodes that are below the section's
heading. That is because there is no further explicit definition embedded into
the document that could force the section to end before the end of its scope is
reached.

- **S3** - By default, the section of a heading includes all of the nodes
  that are below the section's heading.

S3 can therefore be understood to clarify S2 in regards to that particular
case. As such, S3 can be said to define **the default scope** of a section.

Note that S3 is just as clear as S1 since all-of the corresponding nodes are
by default included. In that particular case, a heading's section appears to
be unrestricted (i.e. no "if", no "but" and no "maybe").

Note that the above node order has, at this point, no strict formal definition.
Such a formal definition is however still required since implementations need
to be able to determine if a node is below a particular heading.

<!-- ======================================================================= -->
## the issue with statement-2 (S2)

Despite being able to provide a clear definition for the default scope of a
section, the main issue remains: It is difficult to clarify S2 if a document
contains more than one heading.

However, and based on the use of headings and the general characteristics of
the sections they declare, some clarification is possible:

- **S4** - The nodes below a heading count towards a heading's section up to
  and including the section's last node. Below that last node, no node counts
  towards the heading's section.

As can be seen, further clarification tends to be verbose and is as such more
difficult to clearly understand. In addition to that, S4 is still not clear
since it provides no definition for the last node of a section. S4 simply
assumes that "one just knows" how to identify a section's last node. That
however won't work since implementations need precise instructions.

Obviously, S4 is still just not good enough.
