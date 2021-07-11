
<!-- ======================================================================= -->
# An introduction to headings and sections

Authors use **headings** to group content into **sections**. One can therefore
state that there is some kind of structural relationship between a heading and
the nodes in its section.

Since a heading always defines a section, and since a section can not exist
without a heading, both are said to belong to, or to be **associated** (aka.
related) with each other.

Note that since the most common elements used to form sections are headings,
the following content will, for the sake of simplicity, refer to headings as
the main elements that can be used to group content. However, headings are not
the only elements possible that can be used to form sections.

```
above-below        before-after
===========   or   ==============
A
<h> T </h>         A <h> T </h> B
B
```

And here is where it begins: The only means an author has to state which nodes
are grouped into a section is by the placement of a heading. The order that is
in general agreed upon can be expressed by the following two statements:

- (S1) **The nodes above/before a heading do not belong to its section.**
- (S2) The nodes **below/after** a heading may or may not belong to its section.

S1 is obviously a clear instruction since none of the nodes above a heading
belong to its section. In contrary to that, S2 is not as clear since it does
not clarify which nodes are included and which ones are not.

Even though S2 can not be clarified at this point, one can still state
that any non-empty section has **a first and a last node** and includes
**every other node in between**. As such, a heading's section is in
general understood to consist of consecutive nodes (i.e. no gaps/holes).

Hence, by placing a heading an author uses structure to express which nodes
belong to a section and which ones don't. That is, an author uses the
**structural relationships** between the nodes in order to express his or
her intent. The core purpose of an outline algorithm therefore is to read
these relationships in order to determine to which section (or multiples
thereof) a node within a document belongs.

<!-- ======================================================================= -->
## the document order

In general, a document has a beginning and an end, and therefore like a section
a first and a last node. And since a document has no gaps, the nodes in a
document appear one after another in a consecutive order. For any two nodes
in a document one can therefore state which node is first and which is last.
Because of that, a document is a flat **list of (distinct) nodes**, that can
be described as **a string/sequence of (distinct) nodes**.

```
n1.............. h T nX ......... nZ
|-document-order-------------------|
|-above/before-|     |-below/after-|
```

Based on that, a document corresponds with **a total order of nodes**. Since
that node order defines which nodes are above/below a heading, it may also be
referred to as **the document order**, as **the above/below node order** or
as **the before/after node order**. That is, these descriptions can be used
to refer to the same "thing".

Similar to a document, a section has a first and a last node, and contains all
the nodes in between. Because of that, a section has **no gaps**. Consequently,
and in regards to a document order, a section is **a substring of nodes**. A
section can therefore be described as a total suborder that is embedded into
the document order.

<!-- ======================================================================= -->
## no trivial generic answer

The focus is at this point on statement S1 that can be rephrased as follows:

- (S1) Node `n` does not belong to section `h`, if `(n above-of h)` is true.

Since a human only needs to "just look at the placement" of a node in order to
determine if it is above or below a heading (i.e. `(n above-of h)` is true or
not), one might assume that an implementation should be able to make that
determination just as easily.

```
                                                   p
A                       |-> A                      |
<h> T </h>    <=>    p -|-> h -> T    <=>     -----------
B                       |-> B                 |    |    |
                                              A    h    B
                                                   |
                                                   T
```

The issue is however that an implementation does not see a document as a flat
list of nodes that begins at the top and ends at the bottom. An implementation
sees fragments such as the above as the nodes of a document tree and therefore
nodes `A`, `h` and `B` as child nodes to a common parent node `p`.

So how can an implementation determine if a node is above or below a heading?
That is, how can an implementation determine if the expression `(A above-of h)`
is true or not? And what is the meaning of "above" in the context of a tree?
After all, node `A` is a sibling of `h` and therefore not strictly "above" it.

Note that parent node `p` is "clearly" above heading `h`, which would suggest
that the answer of the first question is, at least in regards to node `p`,
simple and straight forward.

Since there does not seem to be a simple mapping of the "above" node order onto
the node order of a document tree (or vice versa), one can assume that Mathematics
(in particular "Order Theory") must be used in order to answer the above questions.
That is, to answer these kind of questions orders of nodes need to be transformed,
compared and combined. In other words, even though inaccurate simplifications are
in general possible, there is no direct simple answer.
