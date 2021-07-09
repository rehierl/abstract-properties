
<!-- ======================================================================= -->
# A stream-based point of view

An implementation must **visit all the nodes in an orderly fashion** (i.e. one
after another) since it needs to guarantee that it will not visit the content
nodes of a section before it has reached a section's sectioning node.

After all, if an implementation would reach a section's first node before its
sectioning node, it could not be aware that the section even exists. In such
a case, one might be unable to identify the first node of a section as the
section's actual first node.

```
.., h, T, nF,..,nL, .. <= document order
    |<-?->|-scope-|    <= scope of section-A
   open       close    <= open/close events
```

As soon as an implementation reaches a heading, it needs to determine which
operations to execute in response to reaching that heading. At the very least
an implementation will in general create an object in order to represent the
section. In addition to that, an implementation may mark the section as being
**known** (aka. introduced/declared) and **open**.

Likewise, an implementation can mark a section object as being **closed**,
if it detects that it has moved past the section's last node. Based on these
**states** an implementation can detect the first node (nF) and the last node
(nL) of a section, and by that determine with which node the scope of a section
begins and with which node it ends. These states and the state changes from
one to another can be referred to as **the stream-based perspective** of an
implementation on a section.

Note the underlying transition from the implementation-based towards the
scope-based perspective. That is, every node that is visited while a section
counts as being open, can be understood to be a node in a heading's section,
including a heading and its descendants.

Note that neither the open, nor the closed state are required to be dedicated
properties. For example, a set of section objects may be restricted to all
those sections that still count as being open. In such a case, the "closed"
state of a section could be implemented by removing a section from
**a set of open sections**. Implemented as such, the closed state is then
ambiguous since an implementation can then in general not distinguish between
the states "unknown" and "closed". This issue could however be easily resolved,
if an implementation also maintains **a set of all (known) sections**,
regardless of which state they are in.

<!-- ======================================================================= -->
## sections as substrings

Both state changes (i.e. do-open and do-close) can be understood to define a
prefix and a suffix to the node order of a document, each of which contain all
the nodes that are not within the scope of a section. The prefix ends as soon
as a section is opened, and the suffix begins as soon as a section is closed.

Because of that, and in regards to a document order, the **scope** of a section
can be said to be **defined in terms of all the nodes it does not contain**
(i.e. a removal-based definition). Put differently, a section can be said to
contain all the nodes that are visited while the section counts as being open.

Note that the first-to-last point of view can be understood to define a closed
interval (e.g. `scope := [first,last]`) over the node order of a document. In
contrary to that, the removal-based point of view can be said to define two
intervals: (1) no node belongs to a section until the section counts as being
open (e.g. `prefix := (-inf,open)`), and (2) no node belongs to a section once
the section counts as being closed (e.g. `suffix := [closed,+inf)`).

* document := prefix × scope × suffix

Since only a prefix and/or suffix is removed, a section is a **substring** to
the document order. As such, a section may in general also be referred to as
**an ordered sub-sequence of nodes**.

Note that this removal-based perspective does support empty sections since a
section is empty if the document is equal to the concatenation of the above
prefix and suffix (i.e. an empty scope).

```
... h T ..... nX ...
    |-scope----|
    open   close
```

Due to the above, a section can be understood to contain its sectioning node
and its descendants. Because of that, implementations will have to classify
the nodes within a section as **control nodes** and **content nodes**.

Note that, as a matter of clarity, the **default perspective** may be referred
to as the **scope-based perspective** in order to distinguish it from this
stream-based perspective.

Note that neither the scope-based nor this stream-based perspective support
sections that have gaps. That is, a heading and the nodes associated with it
form **a composite unit** (i.e. in regards to a document order one continuous
sequence/stream of nodes). Based on that, a sectioning node and the content
nodes associated with it, can not be split apart.
