
With regards to a consistent setup, the following references may be used:

* The sequence, to which another sequence is its parent sequence,
  is said to be one of the parent sequence's child sequences.
* All the subsequences of a sequence
  are said to be the sequence's inner or descendant sequences.
* A sequence to which another sequence is a descendant sequence
  is said to be one of the sequence's outer or ancestor sequences.
* A sequence that has no outer sequence is said to be a root sequence.
* Two sequences that have the same parent sequence
  are said to be sibling sequences.

(simple) hierarchies:

* A set of sequences that has no more than one root sequence
  is said to be a hierarchy of sequences.
* A set of sequences that has more than one root sequence
  is said to be a forest of hierarchies.

Note that a root sequence is no subsequence to any other sequence than itself.

strict hierarchies:

* A strict hierarchy is based upon the `strict-subsequence-of`
  operator instead of the "simple" `subsequence-of` operator.
* A strict hierarchy is a hierarchy in which each sequence has
  one or more elements that none of its strict subsequences has.
* That is, any subsequence is a strict subsequence to all of
  its ancestor sequences.
* A strict forest of hierarchies is a forest of hierarchies
  in which each hierarchy is strict.

Note that a root sequence is no strict subsequence to any sequence,
including itself.

Note that a strict hierarchy is also a simple hierarchy.
