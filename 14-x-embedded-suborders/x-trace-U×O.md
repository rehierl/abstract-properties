
* thus far the focus was on (n × c)
* (s) was ignored thus far - what about (s) ?!?
* note - similar to "inner set" and "outer set"
* here - "unordered set" vs. "ordered set"

note the thought
- (1) the trace of a node - by default in regards to the nodes in the
  unordered doctree - maps to a substring in the pre-order trace
- then (2) - the trace of a node in regards to the ordered doctree
- (1) is a prefix to (2)
- the last step before introducing types of scopes

<!-- ======================================================================= -->
## a node's induced subtree in an ordered tree

```
             p                      |-tO[n]---------------|
             |                      ||-------------tU[n]-||
 ==========================         || n =|=> (fc .. lc) ||
 | .. |       |      | .. |         ||----|--------------||
 |    | |-------------------|       |     |=> (ns .. ls)  |
 fs  ps ||-tU[n]---| ns  ls |       |---------------------|
        ||    n    |        |
        ||    |    |        |
        || ======= |        |
        || | ... | |        |
        || fc   lc |        |
        ||---------|        |
        |-------------tO[n]-|
```

Recall that the scope of a tag corresponds with an induced subtree in the
un-ordered tree. That is, it contains the tag's defining node and all of
its descendants in the node order of that tree. Because of that, it is more
accurate to define the pre-order trace of a tag `trace(n)` as the trace
`traceU(n)` of the induced subtree `tU[n]` in the un-ordered tree `tU`.

* `traceU(n) := n × traceU(fc) × ... × traceU(lc)`

However, since a node has even more descendants in an ordered tree (i.e. its
former subsequent siblings and their descendants), a node can also be said to
define a second induced subtree `tO[n]` in the ordered tree `tO` and, based
on that, can be said to have a second pre-order trace `traceO(n)` associated
with it. Because of that, a node can be understood to be associated with two
distinct pre-order traces, each of which is formed from a well-defined set of
nodes in the corresponding tree.

<!-- ======================================================================= -->
## a node's second pre-order trace

```
<r> ..                  <n> ..        </n> ..      </p> .. </r>
-|-----------------------|--------------|------------|-------|-
 r × .. p × (fs .. ps) × n × (fc .. lc) × (ns .. ls) × ..
-----------------------|----------------|------------|---------
                       |<- traceU(n)  ->|            |
                       |<- prefix     ->|<- suffix ->|
                       |<- traceO(n)               ->|
```

Due the pre-order rule prefixing a sequence of former subsequent siblings with
a sequence of former child nodes and their descendants, a the pre-order trace
of a node in regards to the un-ordered tree `traceU(n)` is a prefix to the
node's pre-order trace in regards to the ordered tree `traceO(n)`.

* `traceO(n) := (prefix × suffix)`
* `(traceU(n) prefix-of traceO(n))`

One might now notice that the trace of a node `traceU(n)` is followed by the
trace of its former next subsequent sibling `traceU(ns)`. Because of that, the
trace of a node `traceO(n)` can be defined as **a sequence/string of pre-order
traces in regards to the un-ordered tree**.

* `traceO(n) := traceU(n) × traceU(ns) × .. × traceU(ls)`
* `traceO(n) := traceU(n) × traceO(ns)`
* `traceU(n) := n × traceO(fc)`

And since trace `traceO(ns)` is a suffix to trace `traceO(n)`, the traces can
be understood to form **a hierarchy of traces**. That is because all of these
traces can be said to form a family of "nested" sets.

* `(traceO(ns) suffix-of traceO(n))` => `(traceO(n) superset-of traceO(ns))`
* `(traceO(fc) suffix-of traceU(n))` => `(traceU(n) superset-of traceO(fc))`

<!-- ======================================================================= -->
## section-related remarks

Since `traceO(ns)` is a suffix to `traceO(n)` that is prefixed by `traceU(n)`,
`traceU(n)` can be formed from `traceO(n)` by removing `traceO(ns)` as a suffix.

* `traceU(n) := traceO(n) \ traceO(ns)`

Based on that, and if nodes `n` and `ns` are assumed to be headings of equal
rank, then this removal-based operation can be understood as the formal basis
of rank-based headings. That is, **rank values** can be seen as instructions
to close open sections. As such, rank values can be said to restrict default
scopes.

* `section(hi) := (traceO(hi) \ traceO(hj))` if `(rank(hi) <= rank(hj))`

Note that, since a scope is forwards/downwards oriented (i.e. along the edges),
rank values can be said to be **backwards/upwards oriented** (i.e. against the
edges).

Since `traceU(x) := traceO(x) \ trace(y)` will not work if `y` is anything but
a sibling to `x`, trace `traceO(x)` can be said to be formed from **generic
units** (i.e. the traces in regards to the un-ordered tree). Because of that,
one might suspect that a section has a certain level of **granularity**. That
is, depending on a specific context, these building blocks might turn out to
be the atoms (i.e. the smallest indivisible units) of a section.

Note that the hidden attribute/property will turn this intuition into a fact.
