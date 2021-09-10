
<!-- ======================================================================= -->
# An introduction to headings and sections

Authors use **headings** to group content into **sections**. Since the placement
of each heading defines a new section, and since a section can not exist without
a heading, both can be said to be **associated** or **related** with each other.

Note that since the most common elements used to form sections are headings,
the following content will, for the sake of simplicity, initially refer to
headings as the main elements that can be used to group content. One must
however keep in mind that headings are not the only elements possible that
can be used to form sections.

```
above-below
===========
A
<h> T </h>
B
```

And here is where it begins: The only means an author has to state which nodes
are grouped into a section is by the placement of a heading. The order that is
in general agreed upon can be expressed by the following statements:

- **S0** - Sections exist as associated content.
- **S1** - **The nodes above a heading do not belong to its section.**
- **S2** - The nodes **below** a heading may or may not belong to its section.

S0 needs to be understood to be in regards to the placement of a heading and
is because of that in regards to the structural relationship between a heading
and its section. S0 therefore needs to be understood to state that the
structural relationship between a heading and its section can not be ignored.

S1 is obviously a clear instruction since none-of the nodes above a heading
belong to its section. Note that this clarity is a consequence of placing a
heading just above the content it is associated with.

S2 is not as clear as S1 since it does not clarify which nodes are included
and which ones are not. However, one can state that a non-empty section has
**a first and a last node** and includes **every other node in between**.
Because of that, a heading's section can be understood to consist of distinct
consecutive nodes (i.e. **no gaps**, **no holes**). That is, sections are not
arbitrary groups of nodes in the sense that they consist of random nodes.

Hence, by placing a heading an author uses structure to express which nodes
belong to a section and which ones don't. That is, an author uses the
**structural relationships** between the nodes in order to express his or
her intent.

The core purpose of an outline algorithm is therefore to read these structural
relationships in order to determine to which section (or multiples thereof) a
node within a document belongs.

<!-- ======================================================================= -->
## the document order

In general, a document has a beginning and an end, and therefore like a section
a first and a last node. And since a document has no gaps, the nodes in a
document appear one after another in a consecutive order.

For any two nodes in a document one can state which node is first and which is
last. Because of that, a document is a flat **list of nodes**, that can be
described as **a sequence of nodes**, or as **a string of nodes**.

Note that, similar to the components in a sequence, a document consists of
**distinct nodes**. Hence, any document can be said to define a simple set
of nodes and can therefore be described as *a sequence of distinct nodes*.
(Note that these will in general be referred to as **ordered sequences**).

```
n1.............. h T nX ......... nZ
|-document-order------------------>|
|<-------above-|     |-below------>|
```

Due to the above, a document corresponds with **a total order of nodes**. Since
that node order defines which nodes are above a heading, it may also be referred
to as **the document order**, or as **the above-of/below-of node order**.

Similar to a document, a section has a first and a last node, and contains
all the nodes in between. Because of that, a section can be described as
**a substring of nodes** to the document order. As such, a section is a
total suborder that is embedded into the document order.

<!-- ======================================================================= -->
## there is no trivial answer

The focus at this point is on statement S1 which can be rephrased as follows:

- **S1** - Node `n` does not belong to section `h`, if `(n above-of h)` is true.

Since a human only needs to "just look at the placement" of a node in order
to determine if it is above or below a heading, one might assume that an
implementation should be able to make that determination just as easily.

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
nodes `A`, `h` and `B` as the child nodes of a common parent node `p`.

So how can an implementation determine if a node is above or below a heading?
That is, how can an implementation determine if the expression `(A above-of h)`
is true or not? And what is the meaning of that "above" in the context of a
node tree? After all, node `A` is a sibling of `h` and therefore not strictly
"above of" it.

Note that parent node `p` "clearly" appears to be above heading `h`, which
would suggest that the answer in regards to the first question, at least in
regards to parent `p`, is simple and straight forward.

Note that, if parent node `p` is a `<div>` container, then S1 suggests that
such a parent container can not be an element in the heading of a descendant
section. The following discussion will confirm that assumption to be true!

Since there does not seem to be a simple/direct mapping of the above-of node
order onto the node order of a document tree (or vice versa), one can assume
that Mathematics (in particular "Order Theory") must be used in order to answer
questions such as the above. That is, to answer these questions orders of nodes
need to be transformed, compared and combined. In other words, and even though
inaccurate simplifications are in general possible, there is no trivial answer.
