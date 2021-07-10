
<!-- ======================================================================= -->
# Definitions

Since there are several questions that are still undecided, the definitions
below need to be understood to introduce a more general, but still rough
terminology. That is, the exact meaning of the following terms may still
change.

<!-- ======================================================================= -->
## basic terms

The content that is associated with a heading is referred to as a **section**.
Each heading is therefore understood to **introduce**, or to **declare** a new
section. Based on that, a heading can be referred to as a **sectioning node**.

Since a heading always declares a new section, each heading is said to be
accompanied by the section it declares. That is, even if its section has no
content (i.e. is empty), a heading and its section are both said to be
**associated**, or **related** with each other.

- Each heading declares a new section.
- Each section has its own sectioning node.
- One does not exist without the other.

Note that since the relationship between a heading and its section is a strict
**1:1 relationship**, a heading may be identified by its section and vice versa.

Since each section must be declared before it can exist (recall statement S1),
there is a structural relationship between a heading and its section: That is,
a heading always appears **above/before** the first node in its section.

Note that example fragments will use the descendants of a heading to identify
the section it declares. That is, the heading in the following fragment is
said to declare section `T`.

```
 <h> T </h>
|------------|
| section T  |
|------------|
```

**The nodes of a section** are said to be **associated** with it, and also
with the section's heading. As such, the nodes of a section are said to be
**elements in** and also to be located **inside of** the sections to which
they belong. Based on that, a section can be said to **contain** these nodes.

<!-- ======================================================================= -->
## context, scope

```
       |  document  |
-------|------------|---------
       | ...        |
 above | A          | context
-------|------------|---------
       | <h> T </h> |
-------|------------|---------
 below | B          | scope
       | ...        | (from first
       | C          | to last)
       |------------|---------
       | ...        |
```

All the nodes that are above a heading, and which may have some effect on it
and its section, can be understood to define the **context** of a heading and
the nodes within its section.

All the nodes that are below a heading, and that are understood to be inside
of a heading's section can be said to be inside of the **scope** of a heading
and its section. As such, these nodes can be referred to as the **content nodes**
of a heading and its section. That is, the scope of a section begins with its
first content node and ends with its last content node. And since a section
has no gaps, the scope of a section is understood to be **continuous**.

Note that a heading and its descendants can be referred to as **control nodes**
in order to distinguish these from content nodes.

Note that, as an initial assumption, the context of a heading is said to neither
include a heading nor its descendants. Also, none of these nodes are understood
to be within the scope of a heading and its section.

<!-- ======================================================================= -->
## context, scope

At some point a clear description of the document order is required since
"first node" and "last node" would otherwise be without a proper definition.
That is, one must have the means to uniquely identify the first node and the
last node of a section and therefore also all the other nodes in between.

In order to support **empty sections**, the formal definition of a section's
scope will have to be independent of a section's first and its last node.
Requiring these nodes to exist would otherwise disallow empty sections, which
is why one would then have to define what "meaningful content" is (e.g. by
distinguishing between control and content nodes). On top of that, and in
regards to input errors, one can simply not guarantee that a section always
has even one node.
