
<!-- ======================================================================= -->
# A stream-based point of view

An implementation must **visit all the nodes in an orderly fashion** (i.e. one
node after another) since it must be guaranteed that an implementation will not
visit the nodes of a section before it has reached/encountered a section's
sectioning node.

After all, if an implementation would reach a section's first node before its
sectioning node, it could not be aware that the section even exists. In such a
case an implementation would be unable to identify the first node of a section
as its first node.

As soon as an implementation reaches a heading, it needs to determine which
operations to execute in response to reaching that heading. At the very least
an implementation will in general have to create an object of sorts in order
to represent the section. With the creation of such a section object, an
implementation marks the section as being **known** (aka. declared). On top
of that, the section object will used to mark the section as being **open**.

```
... h T nF .... nL ...
    |-scope------|
    open     close
```

Likewise, an implementation can mark a section object as being **closed**,
if it detects that it has moved past the section's last node. Based on these
**states** an implementation can detect the first node (nF) and the last node
(nL) of a section, and by that determine with which node the scope of a section
begins and with which node it ends. These states and the corresponding state
changes between them can be said to form **the stream-based perspective**.

Note that the **first-to-last perspective** may also be referred to as the
**scope-based perspective** in order to distinguish it from this stream-based
perspective.

Note that the issue is not exactly to determine with which node a section does
end, but rather having to determine when no more nodes will be encountered that
count towards a given section. The difference is at this point quite subtle.

Note that any node that is visited while a heading's section counts as being
open is understood to be a node in that section, including the heading and
its descendants.

Note that neither the open nor the closed state are required to be dedicated
properties. For example, a set of section objects may be restricted to all
those sections that still count as being open. In such a case, the "closed"
state of a section could be implemented by simply removing a section from
*a set of open sections*. Implemented as such, the closed state is then
ambiguous since an implementation can then in general not distinguish between
the "unknown" and "closed" states. This issue could however be resolved, if
an implementation also maintains *a set of all (known) sections*, regardless
of which state they are in.

<!-- ======================================================================= -->
## sections as substrings

Both state changes (i.e. do-open and do-close) can be understood to define a
prefix and a suffix to the node order of a document, each of which contains
all the nodes that are not within the scope of a section. The prefix ends as
soon as a section is opened, and the suffix begins as soon as a section is
closed.

- document order := prefix × scope/infix × suffix

Because of that, and in regards to a document order, the **scope** of a section
can be said to be **defined in terms of all the nodes it does not contain**
(i.e. a removal-based definition). Put differently, a section can be said to
contain all the nodes that are visited while the section counts as being open.

Note that the first-to-last point of view can be understood to define a closed
interval (e.g. `scope := [nF,nL]`) over the corresponding document order. In
contrary to that, the removal-based point of view can be said to define two
intervals: (1) no node belongs to a section until the section counts as being
open (e.g. `prefix := (-inf,open)`), and (2) no node belongs to a section once
the section counts as being closed (e.g. `suffix := [closed,+inf)`).

Since only a prefix and/or suffix is removed from the document order, a section
is a **sub-string of nodes** to the document order. Based on that, a section may
also be described as **an ordered sub-sequence of nodes**.

Note that the removal-based perspective does support empty sections since a
section is empty if the document is equal to the concatenation of the above
prefix and suffix (i.e. an empty scope).

<!-- ======================================================================= -->
## no gaps!

```
... h T ... x ... nF ... y ... nL ...
    |-section-------------------|
```

Note that the above stream-based perspective does not support any nodes in
between a section's first content node (nF) and its last content node (nL)
that to not count towards the heading's section (aka. gaps). That is, such
nodes/gaps (y) are not supported.

Likewise, since the heading's section is opened as soon as heading (h) is
reached and closed as soon as the implementation has moved past the section's
last node (nL), these two nodes and all the other nodes in between are counted
towards the heading's section. That is, this stream-based perspective also
does not support any gaps (x) in between a heading's last descendant (T) and
the section's first node (nF).

Due to the above, a heading and all the nodes up until the section's very last
node form **a composite unit** of consecutive nodes. As such, and in regards
to a document order, a section can be described as **a sub-stream of nodes**.

Note that, the support of nodes in between a section's heading and its last
node that do not count towards that section (nodes 'x' and 'y') would require
clear definitions that enable implementations to detect and thus allow to
skip/ignore these nodes in regards to the heading's section.