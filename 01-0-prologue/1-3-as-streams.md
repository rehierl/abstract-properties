
<!-- ======================================================================= -->
# A stream-based point of view

An implementation must **visit all the nodes in an orderly fashion** (i.e.
one node after another) since it must be guaranteed that an implementation
will not visit the nodes of a section before it has reached the section's
sectioning node.

After all, if an implementation would reach a section's first content node
before the section's sectioning node, it could not be aware that the section
even exists. In such a case an implementation would be unable to identify
the first node of a section as its first node.

As soon as an implementation reaches a heading, it needs to determine which
operations to execute in response to reaching that heading. At the very least
an implementation will in general have to create an object of sorts in order
to hold the properties associated with that section (e.g. a title).

With the creation of such an object, an implementation marks the section as
being **known** (aka. declared). In addition to that, the section object will
be used to mark the section as being **open** for associations.

```
n1 ....... h T nF .... nL ....... nZ
           |-scope------|
           open     close
```

Likewise, an implementation will mark a section object as being **closed**,
if it detects that it has moved past the section's last node. Based on these
**states** an implementation can detect the first node (nF) and the last node
(nL) of a section, and by that can determine with which node the scope of a
section begins and with which node it ends. These states, and the corresponding
state changes, can be said to form **a stream-based perspective**.

Note that the stream-based perspective is the reason as to why a section
can be **visualized by simply underlining all the nodes in its scope**.

Note that any node that is reached while a heading's section counts as being
open is understood to be a node in that section, including the heading and
all of its descendants. Put differently, a section is said to contain all
the nodes that will be visited while the section counts as being open.

Note that, since a section counts as being open as soon as the section's
heading is reached, no section can truly be empty. However, one can still
describe a section as being empty, if said section does not contain any
meaningful content (e.g. whitespace only).

Note that the perspective which is based on a section's first and last node
may be referred to as **the scope-based perspective**. This in order to
distinguish it from the above stream-based perspective.

<!-- ======================================================================= -->
## sections as substrings

```
n1 ....... h T nF .... nL ....... nZ
|-prefix--||-scope------||-suffix--|
|-unknown-||-open-------||-closed--|
```

Both state changes (i.e. do-open and do-close) can be understood to define a
prefix and a suffix to the node order of a document, each of which contains
all the nodes that are not within the scope of a section. The prefix ends as
soon as a section is opened, and the suffix begins as soon as a section is
closed.

* document order := prefix ?? scope/infix ?? suffix

Because of that, and in regards to a document order, the **scope** of a section
can be said to be **defined in terms of all the nodes it does not contain**
(i.e. a removal-based definition).

* scope/infix := (document \ prefix) \ suffix

Note that the scope-based perspective can be understood to define a closed
interval (e.g. `scope := [h,nL]`) over the document order. In contrary to
that, the removal-based perspective can be said to define two intervals:
(1) no node belongs to a section until the section counts as being open
(e.g. `prefix := (-inf,h)`), and (2) no node belongs to a section once
the section counts as being closed (e.g. `suffix := (nL,+inf)`).

Since only a prefix and/or suffix is removed from the document order, a
section is a **substring of nodes** to that order. Based on that, a section
may also be described as **an ordered sequence of nodes**.

Note that, since no section is truly empty, and since any section is a substring
to the document order, any section can be understood to be associated with an
**offset and a length** value.

<!-- ======================================================================= -->
## no gaps!

```
n1 ... h T ... x ... nF ... y ... nL ... nZ
       |-section-------------------|
```

Note that the above stream-based perspective does not support any nodes (e.g.
nodes 'x' and/or 'y') in between a section's first content node (nF) and its
last content node (nL) that do not count towards the heading's section (aka.
gaps). That is, such nodes/gaps are not supported.

Likewise, since a section is opened as soon as its heading (h) is reached and
closed as soon as the implementation has moved past the section's last node
(nL), these two nodes and all the other nodes in between count towards the
heading's section. That is, the above stream-based perspective does also not
support any gaps.

Due to the above, a heading and all the nodes until a section's last node
form **a composite unit of consecutive nodes**. As such, and in regards to
a document order, a section can be described as **a sub-stream of nodes**.

Note that, the support of nodes in between a section's heading and its last
node that do not count towards that section (nodes 'x' and 'y') would require
clear definitions in order to allow implementations to detect and thus allow
to skip/ignore these nodes in regards to the corresponding section. However,
such definitions seem futile since one could always argue that the nodes below
a gap effectively form a new section which, as a matter of clarity, should be
introduced as such.

<!-- ======================================================================= -->
## remarks

Note that the issue is not exactly to determine with which node a section does
end, but rather having to **determine when no more nodes will be encountered**
that count towards a given section. The difference is subtle but critical!

Note that, since an implementation is required to perform operations when the
scope of a section is entered, and when its scope is exited, a section can be
said to be **associated with open/close- or enter/exit-events**. Both of these
events must be triggered for each existing section: (1) if the enter-event
isn't triggered, then an implementation is remain unaware that the section even
exists, and (2) if the exit-event isn't triggered, then an implementation will
continue to associate nodes with a section even if that section no longer counts
as being open for associations. Because of that, clear definitions are required
such that an implementation knows when to trigger the corresponding events.

Note that the above states are **not required to be explicit**. For example,
a set of section objects may be restricted to all those sections that still
count as being open. In such a case, the "closed" state of a section could be
implemented by simply removing a section object from "a set of open sections".
Implemented as such, the closed state is then ambiguous since an implementation
can then in general not distinguish between "unknown" and "closed". This issue
can however be resolved, if an implementation also maintains "a set of known
sections", regardless of which states they are in.

Note that, since an implementation will in general **create a section object**
as soon as the section's heading is reached, an implementation can be understood
to associate each node in that section with its section object. With that in
mind, a section object can be understood as **a node property**. Based on that,
the section object can be understood to **emanate** from its heading (as a
node property), and to be **passed on** to all the nodes (one node after
another) that are within the section's scope.

Note that, if implemented as described above, then a subsequent implementation
can easily determine if a node is within the scope of a given section. All it
will have to do is to determine if the corresponding section object is set as a
node property. Based on that, such properties can be seen as **stored results**.

Note that it is in principle non-relevant in which order the nodes in a scope
will be associated. That is because these properties can be understood to
represent simple truth-based values (i.e. inside-of/outside-of) which are set
on all the nodes in a scope. As such, these properties do not reflect an order
of association in any way.
