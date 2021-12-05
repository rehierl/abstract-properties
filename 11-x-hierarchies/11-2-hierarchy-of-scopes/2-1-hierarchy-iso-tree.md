
<!-- ======================================================================= -->
# hierarchy of scopes <=> node tree

The focus of the following is on defining "a hierarchy of scopes" as a class
of setups such that each setup `S` in it allows to form a node tree.

(1) Since each partial setup corresponds with `#RS` node trees, one needs to
require the existence of a dedicated root `r`.

(2) Since each induced sub-setup `S[r]` can be understood to only define the
structure of a tree of `#S[r]` nodes, but does not define the nodes themselves,
one needs to require that each set has a node identifier as its one and only
one CE.

Defined as such, a hierarchy `H` can be understood to holde the definition
of a node tree `T(N,E)`.

In order to show that the transformation from a hierarchy to a tree can be
inverted, one needs to recall that the concept of abstract properties allows
to form a setup of scopes and what the characteristics of these scopes are.

* No scope is empty since each scope is defined as an open interval `[n,*]`.
* The setup must contain `#N` scopes, one for each node in `T`.
* There must be `(#[n,*]-1)` proper sub-intervals for each scope.
* No such sub-interval has `n` as an element.
* `n` is the one and only CE of its scope.

Since the family of scopes formed from a node tree is a hierarchy of scopes,
one needs to show that the entire transformation process from a hierarchy `H`
to a node tree `T` and back to a hierarchy `H*` (i.e. `(H -> T -> H*)`) is
structure preserving.

(A) The one-ce-only requirement of hierarchy `H` guarantees that tree `T` has
`#H` well defined nodes, which is why `(#H == #N)` is true. Furthermore,
hierarchy `#H*` has `#N` distinct sets since one scope will be formed for each
node, which is why `(#N == #H*)` is true, which is why `(#H == #H*)` is true.

(B) For each child set `(c in DS(H))` and its parent set `(p := p(c))` an edge
in `T` is generated from parent node `np := ce(p)` to child node `nc := ce(c)`.
Because of that, `H*` is guaranteed to have a pair of scopes `sp := [np,*]` and
`sc := [nc,*]` such that `sp` is a superset to `sc`.

Based on the definition of "a hierarchy of scopes" and the construction of the
scopes from the generated tree, one can conclude that the resulting hierarchy
`H*` is equal to the source hierarchy `H`. Consequently, `(H* == H)` is true.

Note that, based on the isomorphism described above, each set in "a hierarchy
of scopes" does indeed correspond with the scope of a node in the tree that
hierarchy defines. Hence the "scopes" qualifier in "a hierarchy of scopes".

<!-- ======================================================================= -->
## hierarchy of scopes => node tree

```
S: a rooted normalized setup      T: a node tree
============================  =>  ==============
|-1---------------------|               1
| |-2-----------| |-3-| |             -----
| | |-4-| |-5-| | |---| |             2   3
| | |---| |---| |       |           -----
| |-------------|       |           4   5
|-----------------------|
```

Provided that a given setup `S` is a hierarchy of scopes,
one can form a node tree `T(N,E)` as follows:

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-set-of b) for (a,b in S) }`

<!-- ======================================================================= -->
## node tree => hierarchy of scopes

Given a node tree `T(N,E)`, **a hierarchy of scopes** `S` can be formed using
the concept of abstract properties. That family of scopes can then be used to
define a partial containment order `P(S,<)` using the "superset-of" operator
as the order operator.

Recall that with any digraph, one can always assume the default edge-based
"next-presequent-to" semantics, even though the semantics of a tree can in
general be denoted as the "parent-of" semantics.

```
(a next-presequent-to b)
========================
n1 --|-> n2 --|-> n4
     |-> n3   |-> n5
```

Assume that node `n1` declares property `p1` (i.e. `d(p1) = n1`). According
to the introduction of abstract properties, the scope of `p1` extends over
all the nodes in `T` (i.e. `s(p1) = [n1,*] = {n1,..,n5}`. Put differently,
the scope of `p1` contains every single node in `T`.

Likewise, one can then assume that `n2` declares another property `p2` such
that `d(p2) = n2` and `s(p2) = [n2,*] = {n2, n4, n5}`. One can thus assume
that each and every node `ni` in `T` declares its own property `pi`.

Based on these properties, one can define a set `S` such that it contains the
scope `si` of each property `pi` as an element. As such, set `S` satisfies the
requirements of **a hierarchy of scopes**.

```
S  := +si   := { s1, s2, s3, s4, s5 }
s1 := s(p1) := { n1, n2, n4, n5, n3 } = E(T)
s2 := s(p2) := {     n2, n4, n5     } = [n2,*]
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

<!-- ======================================================================= -->
## derived order relations

A hierarchy of scopes `S` can be used to define an order of scopes `P`.

* `P(S,<)` where `(a < b) := (a superset-of b)`

The tree order order relation `P` of tree `T` can be formed as follows.

* `P(N,E)` where `N := { ce(s) | (s in S) }`
* `E := { (ce(a),ce(d)) | (a ancestor-of d) for (a,d in S) }`

Note that this order relation can also be formed from tree `T`.

* `P(N,E)` where `E :=  { (a,d) | (a ancestor-of d) for (a,d in N) }`
