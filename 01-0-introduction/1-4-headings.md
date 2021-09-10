
<!-- ======================================================================= -->
# An introduction to headings and sections (2)

<!-- ======================================================================= -->
## special case: one heading only

In regards to statement S2 one special case can be highlighted:

If a document has one and only one heading, then the section of that heading is
in general understood to contain all of the nodes that are below the section's
heading. That is because the document then lacks an explicit definition that
could force the section to end before the end of its scope is reached.

- **S3** - By default, the section of a heading includes all of the nodes
  that are below the section's heading.

S3 can therefore be understood to clarify S2 in regards to that particular
case. As such, S3 can be said to define **the default scope** of a section.

Note that S3 is just as clear as S1 since **all-of** the corresponding nodes
are by default included. In that particular case, a heading's section appears
to be unrestricted (i.e. no "if", no "but" and no "maybe").

Note that the above-of node order has, at this point, no strict formal definition.
Such a definition is however still required since implementations need to be
able to determine if a node is below a particular heading.

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

As can be seen, further clarifications tend to be verbose and are as such
more difficult to understand. In addition to that, S4 is still not clear
since it provides no definition for the last node of a section. S4 simply
assumes that "one just knows" how to identify a section's last node. That
however won't work since implementations need precise instructions.

Obviously, S4 is still just not good enough.

Note that the counterpart to S3 (the all-of case) would be, if **none-of**
the nodes below a heading could be allowed to count towards the section of
a particular heading. Such a statement would be just as clear as S3 since
it would then also be with no exception. In contrary to that, S4 represents
a **some-of** quantifier since it effectively represents the "some but,
not all" case.

Note that these quantifiers (i.e. all-of, none-of, some-of) are at the very
core of this discussion. As one might already assume, the difficult to define
some-of quantifier can be defined in terms of an all-of (i.e. all included
up to a certain point) and a none-of (i.e. none of after that) quantifier,
both of which will build upon well-defined suborders.
