
<!-- ======================================================================= -->
# (ordered) sequence of siblings

```
a path graph            a child order        a rooted tree: r ->
=================  <=>  ==============  <=>  ===================
r -> c -> .. -> l       c1 -> .. -> cN       -> c1 -> ... -> cN
```

Recall that an ordered sequence of nodes defines a total order of nodes, which
is why each ordered sequence corresponds with a path graph. As such, an ordered
sequence of nodes can be understood to begin with a root `r`, continue with a
child `c` and end in a leaf `l`. Consequently, an ordered sequence can be seen
as defining a rooted path `rp`, which is why this **path-based perspective**
can be understood to represent **a vertical point of view**.

* `s := (s1,..,sN)` <=> `rp := (r,c,..,l)`

In contrary to that, an ordered sequence can also be understood to define
a child order. That is, each element in it can be seen as the child of a
virtual root node, which is why an ordered sequence can be described as
**a sequence of siblings**. This **child/sibling-based perspective** can
therefore be understood to represent **a horizontal point of view**.

* `s := (s1,..,sN)` <=> `co := (c1,..,cN)`

Note that, in the context of this discussion, the description as "a sequence
of siblings" must be understood with **a more general point of view** in mind.
That is, a sequence of siblings is not necessarily a sequence such that each
node in it is a sibling according to the current node order in question.
Instead, that description focusses more on some common characteristic of the
nodes contained within such an ordered sequence - e.g. "siblings in the
previous node order".

Based on the above, a rooted path can also be described as the concatenation
of one or more child orders.

* `s := (s1,..,sN)` <=> `rp := (r) × (c) × .. × (l)`

Also note that embedding a child order into a tree which has one parent node
only (i.e. its root), will turn the tree into a path graph that corresponds
with an ordered sequence.

* `{(r,c1),..,(r1,cN)}` + `{(c1,c2),..,(cN-1,cN)}` => `{(r,c1),(c1,c2),..}`
* `s := (s1,..,sN)` <=> `s := (r,c1,..,cN)`

Note that subsequent discussions will treat the child/sibling-based perspective
as **the default point of view**. That is, ordered sequences will be treated as
sequences of siblings.

<!-- ======================================================================= -->
## tree traversal

In the end, the purpose of embedding even more nod orders into a tree order
is to turn a tree into a path graph. As such the tree will correspond with
an ordered sequence of nodes. Because of that, the resulting ordered sequence
of nodes will represent **a (traversal) trace of nodes** such that it can be
understood to be defined based on the node orders that were embedded one after
another.

Note that the transformation of a tree into a trace of nodes is, regardless
of any immediate practical use, a theoretical approach which focusses on
explaining **the inner structure of such a trace** of nodes.

<!-- ======================================================================= -->
## narrow down the width

```
     r               r
     |               |
  --------    =>   |---|
  |     |          | . |
|---| |---|        | . |
| . | | . |        |---|
| . | | . |
|---| |---|
```

The subsequent embedding of more and more node orders can be understood to
narrow down the width of a tree until what remains is effectively
**a rooted path**.

<!-- ======================================================================= -->
## flatten the height

```
       |----|               |----|
r -|-> | .. |    =>    r -> | .. |
   |   |----|               |----|
   |-> | .. |
       |----|
```

The subsequent embedding of more and more node orders can be understood to
flatten the height of a tree until what remains can essentially be referred
to as **a child order** and thus as a sequence of siblings.

<!-- ======================================================================= -->
## sequences of (subsequent) siblings

```
general node order pattern             |  in short
====================================   |  ===========
p -> (fs .. ps) -> n -|-> (ns .. ls)   |  n -|-> s(n)
|..   |..   |..       |-> (fc .. lc)   |     |-> c(n)
```

In the following discussion, and regardless of their own (former first) child
nodes, `ns` and `fc` can both be described as heads of **sequences of siblings**
(i.e. `ns*` and `fc*`) and can as such be used to refer to the corresponding
ordered sequences of nodes. That is, descriptions such as "last subsequent
sibling" in regards to the head of a sequence of siblings must be understood
to refer to the last subsequent sibling that can be reached beginning with
the corresponding node while moving into the same "direction". That is,
assuming that these nodes do exist.

* The last subsequent sibling of `ns*` is `ls`.
* `s(n) := ns*` and `c(n) := fc*`

Note that these sequences of siblings are total sub-orders to the resulting
tree order. However, each node within a sequence of siblings may in general
still have up to two child nodes - i.e. its former next sibling, and its
former first child - the latter of which will in general be omitted.

Note that the sequence of subsequent siblings of a subsequent sibling (i.e.
`s(n)`) is a suffix to the sequence of subsequent siblings of a presequent
sibling (i.e. `s(p)`). In contrary to that, the sequences of former child
nodes of two siblings are disjoint.

* `(s(n) suffix-to s(p))`
* `(c(n) disjoint-to c(p))`

<!-- ======================================================================= -->
## last (subsequent) siblings

Similar to the root of an ordered doctree, the former **last sibling** of a
node has **no more than one child** (i.e. its former first child). That is
because the last subsequent sibling of a node, like the root of a tree, has
no further subsequent sibling and therefore no such sibling as its child.

* `ls` and `lc` have themselves no more than one child

Since the last nodes of such sequences are the only nodes in an ordered doctree
that may have no child at all, the **leaf nodes** of an ordered doctree all are
last nodes to such sequences. That is because every other node has at least one
child (i.e. its former next sibling).

These leaf nodes are therefore the only ones left which still need to be
connected in order to form a trace of nodes.

* `ls` and `lc` may be leaf nodes of the ordered doctree
* each last node of a sequence of siblings is a possible leaf
