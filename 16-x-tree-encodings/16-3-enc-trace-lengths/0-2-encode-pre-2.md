
<!-- ======================================================================= -->
# howto form the length-based encoding in pre-order

Even though the theoretical aspects of a sequence of length values have been
explained already, there still is the question of how an implementation can
form the sequence of length values `len(T)` of a document tree `T(N,E)` such
that no excessive runtime complexity is required.

<!-- ======================================================================= -->
## a top-to-bottom based approach

```
          | S1    | S2     | S3      | S4       | S5        | S6
========================================================================
 A        | sA: A | sA: AB | sA: ABC | sA: ABCD | sA: ABCDE | sA: ABCDEF
--------- |       | sB: B  | sB: BC  | sB: BCD  | sB: BCDE  | sF: F
 B     F  |       |        | sC: C   | sD: D    | sD: DE    |
------    |       |        |         |          | sE: E     |
 C  D     |
   ---    | set of finished traces (Hpre)
    E     |=============================================================
          |       |        | tC: C   |          | tE: E     | tF: F
          |       |        |         |          | tD: DE    | tA: ABCDEF
          |       |        |         |          | tB: BCDE  |
```

Note that the following steps will be executed during a pre-order traversal.

* step-0: One first begins with an empty set of (unfinished) traces `S0`.
* step-1: The next step begins by initializing a new set of traces `S1` by
  cloning `S0`. And since the first node visited in the pre-order traversal
  is the doctree's root, an empty sequence `sA` is created and added to `S1`.
  As a final operation, this step appends node `A` to each sequence in `S1`.
* step-2: As before, the previous set of traces is cloned to initialize a new
  set of traces `S2`. And since this step visits node `B`, an empty sequence
  is created and added to `S2`. This step then finishes by appending `B` to
  each sequence in `S2`.
* step-X: The overall operations performed by each step can be described to
  (1) clone the previous set of traces `Si` in order to initialize the next
  set `Sj`, then (2) to add a new empty sequence `sX` to `Sj` for node `X`,
  which is being visited, and (3) to append node `X` to each sequence in `Sj`.
* step-3: Once the basic overpations have been executed, the process concludes
  that it has finished to visit node `C`. Since no more descendant of `C` will
  be visited, sequence `sC` is complete, which is why `sC` can be removed from
  `S3` and added to a set of finsihed traces `Hpre` as trace `tC`.

Note that the following general steps will be repeated for each node `X`:
(1) clone `Si` to initialize `Sj`, (2) add the empty sequence `sX` to `Sj`,
(3) append `X` to each sequence in `Sj`, and (4) if no more descendants of
`X` will be visited, move `sX` from `Sj` into `Hpre`.

<!-- ======================================================================= -->
## a stack of open scopes (Si)

```
  S3     |   -->   | S4              S5       |    -->    | S6
==============================     ====================================
 sA: ABC | sA: ABC | sA: ABCD       sA: ABCDE | sA: ABCDE | sA: ABCDEF
 sB: BC  | sB: BC  | sB: BCD        sB: BCDE  |           | sF: F
 sC: C   |         | sD: D          sD: DE    |           |
         |         |                sE: E     |           |
```

As described above, each node `n` will be appended to all the sequences of each
node in `A*(n)`. In addition to that, once all the nodes in `D*(n)` have been
visited, the trace of the corresponding node `tn` is done, which is why it can
be removed from the set of current sequences `Si` and added to the set of
completed pre-order traces `Hpre`.

At this point one can notice that the set of unfinished sequences consists of
those sequences that belong to all of the nodes in the current **rooted path**
`rp(n)`. This shouldn't be surprising since these are the nodes whose scopes
have not yet been exited. Because of that, the enter event and the exit event
of each scope will have to be used to update `Si`, which can now be described
as **a stack/path of open scopes**.

<!-- ======================================================================= -->
## a stack/path of node counts (Ci)

```
  C3       |    -->    | C4        | C5        |    -->    | C6
========================================================================
 n:  ABC   | n:  ABC   | n:  ABCD  | n:  ABCDE | n:  ABCDE | n:  ABCDEF
 cA: (1,3) | cA: (1,3) | cA: (1,4) | cA: (1,5) | cA: (1,5) | cA: (1,6)
 cB: (2,2) | cB: (2,2) | cB: (2,3) | cB: (2,4) |           | cF: (6,1)
 cC: (3,1) |           | cD: (4,1) | cD: (4,2) |           |
           |           |           | cE: (5,1) |           |
========================================================================
   len: (x,x,1,x,x,x) >|               len: (x,4,1,2,1,x) >|
```

Since the trace of each node `pre(n)` is a substring to the traces of its
ancestors, each trace can be understood to be associated with a unique
offset in regards to the document tree's pre-order trace `pre(T)`. Because
of that, the process can be altered to maintain an offset for each node.

Furthermore, the process is not required to produce actual sequences since
each trace contains its defining node and all of the other nodes up until its
last node. That is, the trace of a node `pre(n)` can be described in terms of
an offset `o` and a node count `c`.

The process can therefore be reduced such that it operates on a stack of node
counts, each of which is associated with the node's offset in the document
tree's preorder trace - i.e. `s(n) := (o,c)`.

For obvious reasons, the process must now produce the document tree's trace
`pre(n)` (aka. `n(T)`) and a sequence of length values `len(T)`. The latter
of which must be updated each time the scope of a node is exited.
