
<!-- ======================================================================= -->
# trees in set theory (ST)

- both concepts (AST + DST) focus on prefixes
- since maths needs to deal with sets of infinite size
- downwards - smaller numbers are less significant
- upwards - larger numbers are more significant

<!-- ======================================================================= -->
# trees in descriptive set theory (DST)

- a collection of (ordered) sequences
- each prefix of every sequence must be an element

Note that ..

- ordered based on the "prefix-of" operator
- each sequence/prefix corresponds with a rooted path

<!-- ======================================================================= -->
# trees P(T,<) in axiomatic set theory (AST)

- `ht(t) := { (s in T) | (s < t) } := [*,t]` must be well-ordered
- well-ordered := total + each subset hat a least

Note that ..

- ht() is always of finite size
- ht() decreases in size towards the root
- ht() corresponds with a rooted path
- ht() can be described as a reversed scope

Note that `ht()` corresponds with the set of nodes of the corresponding rooted
path in a node tree. As such it can be described as as downward-open interval.
Hence the description as **a reversed scope**.
