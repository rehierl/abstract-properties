
Note that this is a past version of a brainstorming process in regards to
the length-based encoding of node trees.

<!-- ======================================================================= -->

In a strict setup, the following is true:

* Two distinct sets in a strict setup are either disjoint,
  ex-or one set is a strict subset of the other.

If a given setup is guaranteed to be strict,
then the following simplification is possible:

1. Find an element that two distinct sets have in common.
2. If there is no such element, then both sets are disjoint.
3. If such an element is found, then the larger set is the super-set.

Extended

1. Pick an element.
2. Find all the sets that contain this element.
3. Sort these sets according to their size (in descending order).
4. This ordered list of sets is a top-down path in the resulting tree.
5. The chosen element is an element of the smallest set's
   identifying/characteristic subset (iss/css).
6. Rinse and repeat.

Extended

0. The iss/css of each set is initialized with the set itself.
1. Once you have a path, remove the chosen element
   from the iss/css of the smallest set's ancestor set.

<!-- ======================================================================= -->

```
                     outer sequences      outer sequences
node tree            enter-order          exit-order
=================    =================    ==============================

 A                   A B D G E H C I F    G D E B H I F C A - NS
=================    =================    ================= - A
 B      H   C          ======= = =====    ======= = =====   - B, H, C
======     ======        === =     = =    === =     = =     - D, E, I, F
 D  E       I  F           =              =                 - G
===
 G
```

Given the above set of sequences, and without any additional information (i.e.
which node within a sequence is its defining node), the initial node tree can
be reconstructed. In order to reconstruct the initial tree, one has to know
(1) the parent sequence and (2) the next/previous sibling of each sequence.

The relevant steps to read a tree from such a hierarchy are:

* (1) Determine the root sequence.
* Note that the root sequence alone is not sufficient to reconstruct the tree.
* (2) Determine the parent sequence of each sequence.
* Note that each sequence is shorter than its parent sequence.
* (3) Determine the node order based on the starting position of each sequence.
* Note that each sequence has a unique position within the root sequence.
* Note that the position of each sequence corresponds with the node order.
* Note that this step fixes the order of child nodes within each parent.

<!-- ======================================================================= -->
## What if the node order would correspond with the exit-order instead?

Each node can still be understood to represent two sequences of nodes: (S1) the
sequence that begins with the descendants of a node and that ends in the node
itself, and (S2) the sequence that only contains the node's descendants and
that does not end in the node itself.

Note that, instead of being a suffix, S2 is now a prefix of S1.

Note that the exit-order states that ancestors are subsequent to their
descendants. In contrary to that, the enter-order states that descendants
are subsequent to their ancestors.

```
                     outer sequences      outer sequences
node tree            enter-order          exit-order
=================    =================    ==============================

 A                   A B D G E H C I F    G D E B H I F C A - NS
=================    =================    ================= - A
 B      H   C          ======= = =====    ======= = =====   - B, H, C
======     ======        === =     = =    === =     = =     - D, E, I, F
 D  E       I  F           =              =                 - G
===
 G
```

Note that the following is with regards to reading all outer sequences of the
exit-order in first-to-last (i.e. left-to-right) order.

Given the above set of sequences, and without any additional information (i.e.
which node within a sequence is its defining node), the initial node tree can
still be reconstructed:

* (1) Determine the root sequence.
* Note that, as before, the root sequence is the longest sequence.
* (2) Determine the parent sequence of each sequence.
* Note that multiple sequences may have the same position within the root.
* Note that the position of a sequence within its parent is still unique.
* (3) Determine the node order based on the position of each sequence.

Solely based on a hierarchy of sequences, an algorithm can
reliably distinguish between the enter- and the exit-order:

(1, enter-order)

* subsequences have unique positions within the root
* prefix, no - the root never begins with a subsequence
* suffix, yes - the root always ends with a subsequence

(2, exit-order)

* subsequences may have the same position within the root
* prefix, yes - the root always begins with a subsequence
* suffix, no - the root never ends with a subsequence

Note that the root either has no prefix (ex-)or no suffix. Also note
that the same applies to any sequence that has more than one element.

**CLARIFICATION**
A rooted ordered tree of nodes can be defined as an ordered list of nodes in
combination with a list of (offset,length) pairs which define the subsequences
with regards to the root sequence.

Note that the offset of each pair is actually not required as (N-1) subsequences
are required. That is, an ordered list of (N) nodes in combination with an
ordered list of (N-1) length values is sufficient to unambiguously define a
node tree.

<!-- ======================================================================= -->
## And what if all sequences are flipped?

```
                     outer sequences      outer sequences
node tree            enter-order          exit-order
=================    =================    ==============================

 A                   A B D G E H C I F    G D E B H I F C A - NS
=================    =================    ================= - A
 B      H   C          ======= = =====    ======= = =====   - B, H, C
======     ======        === =     = =    === =     = =     - D, E, I, F
 D  E       I  F           =              =                 - G
===
 G
```

Note that, if all sequences of the exit-order are flipped (`s'[i] = s[#s-1-i]`),
then the resulting hierarchy has the same characteristics as if it were a
enter-order hierarchy: never a prefix, but always a suffix.

```
outer sequences      outer sequences      flipped outer sequences
enter-order          exit-order           exit order
=================    =================    ==============================

A B D G E H C I F    G D E B H I F C A    A C F I H B E D G - NS
=================    =================    ================= - A
  ======= = =====    ======= = =====        ===== = ======= - C, H, B
    === =     = =    === =     = =            = =     = === - F, I, E, D
      =              =                                    = - G
```

Even though the flipped hierarchy is not identical to the enter-order hierarchy
(i.e. the enter-order hierarchy is not symmetrical to the exit-order hierarchy),
the original node tree can still be reconstructed, if the children of a node
are added in reverse order (i.e. prepend instead of append).

Consequently, the same algorithm that is used to reconstruct the node tree from
the enter-order hierarchy can be used to recreate the node tree from the flipped
exit-order hierarchy, if the child nodes are added in the corresponding order.
Likewise, the same applies to flipping the enter-order hierarchy.

As a result, and if the order of a hierarchy is known, then the more efficient
algorithm can be used to reconstruct a tree.

<!-- ======================================================================= -->
## And what if inner sequences are used instead?

```
                     inner sequences    inner sequences
node tree            enter-order        exit-order
=================    ===============    ======================

 A                   B D G E H C I F    G D E B H I F C - NS
=================    ===============    =============== - A
 B      H   C          =====     ===    =====     ===   - B, C
======     ======        =              =               - D
 D  E       I  F
===
 G
```

Assumed that the empty inner sequences of leaf nodes are omitted.

(1, enter-order)

* a sequence has no suffix, if the nodes's last child is a leaf

(2, exit-order)

* a sequence has no prefix, if the node's first child is a leaf
