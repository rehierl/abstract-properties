
<!-- ======================================================================= -->
# hierarchy of scopes <=> node tree

The focus of this chapter was to define "a hierarchy of scopes" as a class of
setups such that each setup `S` in it allows to form a node tree.

(1) Since each partial setup allows to form a forest of `#RS` trees, one needs
to require the existence of a dedicated root set `r`.

(2) Since each induced sub-setup `S[r]` can be understood to only define the
structure of a tree of `#S[r]` nodes, but does not define the nodes themselves,
one needs to require that each set has a node-id as its single CE.

Defined as such, each hierarchy `H` can be understood to define a tree `T`.

In order to proof that the transformation from a hierarchy to a tree can be
inverted, one needs to recall that, using the concept of abstract properties,
a setup of scopes can be formed, and what the properties of these setups are.

* No scope is empty since each scope is defined as an open interval `[n,*]`.
* The setup will hold one scope per node.
* There are `(#[n,*]-1)` sub-intervals for each scope `[n,*]`.
* No such sub-interval has `n` as an element.
* `n` is the CE of `[n,*]`.

Since the family of scopes formed from a node tree is in fact a hierarchy of
scopes, one needs to show that the entire process (i.e. `(H -> T -> H*)`) is
structure preserving.

(A) The one-ce-only requirement of `H` guarantees that `T` has `#H` nodes.
Because of that, `(#H == #N)` is true. Furthermore, the family of scopes has
`#N` distinct sets since one scope will be generated for each node. Because
of that, `(#N == #H*)` is true. Consequently, `(#H == #H*)` is true.

(B) For each child set `(c in DS(H))` and its parent set `(p := p(c))` an edge
in `T` is generated from the parent node `np := ce(p)` to the corresponding
child node `nc := ce(c)`. Because of that, `H*` is guaranteed to have a pair
of scopes `sp := [np,*]` and `sc := [nc,*]`. Consequently, `sc` is equal to
child set `c`.

Based on the definition of "a hierarchy of scopes" and the construction of the
scopes from the generated tree, one can conclude that the resulting hierarchy
`H*` is equal to the source hierarchy `H`. Consequently, `(H* == H)` is true.

Note that, based on the above isomorphism, each set in "a hierarchy of scopes"
does indeed correspond with a scope in the tree that hierarchy defines. Hence
the "scopes" suffix in "hierarchy of scopes".

<!-- ======================================================================= -->
## hierarchy of scopes => node tree

```
S: a rooted normalized setup      T: a node tree
============================  =>  ==============
|-1---------------------|             1
| |-2-----------| |-3-| |           -----
| | |-4-| |-5-| | |---| |           2   3
| | |---| |---| |       |         -----
| |-------------|       |         4   5
|-----------------------|
```

Provided that a given setup of sets `S` has (1) one root set only, and (2)
a unique node identifier as the CE of each set, one can use `S` to form an
order of scopes `P(S,<)` ..

* `P(S,<)` where ..
* `(a < b) := (a strict-superset-of b) for (a,b in S)`

.. and also a node tree `T(N,E)`.

* `T(N,E)` where `N := U(S)` and ..
* `E := { (ce(a),ce(b)) | (a parent-set-of b) for (a,b in S) }`

<!-- ======================================================================= -->
## node tree => hierarchy of scopes

Given a node tree `T(N,E)`, **a family of scopes** `S` can be formed based on
the concept of abstract properties. That family of scopes can then be used to
form a strict partial containment order `P(S,<)` using the "strict-superset-of"
operator as the order operator.

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
that each and every node `ni` in `T` declares its very own property `pi`.

Based on these properties, one can define a set `S` such that it contains
the scope `si` of each property `pi` as an element. As such, set `S` can be
described as **a family of scopes**.

```
S  := +si   := { s1, s2, s3, s4, s5 }
s1 := s(p1) := { n1, n2, n4, n5, n3 } = E(T)
s2 := s(p2) := {     n2, n4, n5     } = [ni,*]
s3 := s(p4) := {         n4         }
s4 := s(p5) := {             n5     }
s5 := s(p3) := {                 n3 }
```

One can then define a containment order `P` using the family of scopes `S`.

* `P := (V,<)` such that `(V := S)` and
* `S := { si | (si := [ni,*]) such that (i in [1,#V(T)]) }`
* `(a < b) := (a strict-superset-of b)`
