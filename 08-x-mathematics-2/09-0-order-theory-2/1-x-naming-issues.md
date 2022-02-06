
<!-- ======================================================================= -->
# the difficulties with naming "things"

As one was able to see with the definition of downward-/upward-total, maths
has its own way of naming things, heavily influenced by the focus on numeric
values. In contrary to that, computer science has its own way to name the
things that are in its focus. For obvious reasons, this makes it difficult
to name things such that people from both groups can intuitively understand
the meaning of a statment. Especially, if one group has a point of view that
is upside-down to the point of view of the other group.

<!-- ======================================================================= -->
## prefix-/suffix-order (don't use !)

A downward-total poset may be described as **a prefix order**.
Likewise, an upward-total poset may be described as **a suffix order**.

Note that the description as "prefix/suffix order" is **misleading**, since
these are structural definitions (i.e. downward-/upward-total) and as such
independent from the elements the order contains. Because of that, the use
of these terms should be avoided. Instead, one should use alternative
descriptions such as **a downward-/upward-total poset**.

Note that "prefix" in "prefix order" needs to be seen in regards to some
rooted path over a tree. Likewise, "suffix" in "suffix order" needs to be
seen in regards to the path that begins in a node and ends in a leaf.

Note that an induced subtree can be seen as a suffix to a tree. Likewise,
a rooted path can be seen as a (special) prefix. However, these extended
definitions of prefix/suffix have nothing to do with the description as
"a prefix-/suffix-order".

<!-- ======================================================================= -->
## example - upwards vs. downwards

As mentioned before, the concepts used in the context of this discussion are
heavily influenced by a numerical point of view. Amongst other definitions,
this defines to see larger numbers as "upwards" and therefore also as "more
significant" due to their larger value.

In computer science it is upside-down since the least element (maths pov) of
a tree is in general drawn at the very top and also named as the root element.
Furthermore, that root is seen as the most significant node of a tree.

The issue with that is how to name things, if it turns out that one of the
two groups didn't develop an analogous counterpart to a definition of the
other group. Take the definition of "downward-total" for example, which
reflects a numerical point of view.

The definition of "prefix order" seems as an attempt to name the same thing
using the language of computer science. The issue here is however, that it
fails to properly grasp the aspect of a "total suborder". In addition to that,
it coins the term "prefix" and also "suffix" with a particular meaning, which
stands in the way of an extended point of view on prefixes and suffixes.

Because of that, and since computer science still needs to adopt to seeing
the orders behind graph-like structures, the mathematical point of view on
"downward-total" still seems more appropriate. In other words, computer
science would in general be well advised to adopt to a more mathematical
point of view, especially on generalized lower levels of abstraction.
