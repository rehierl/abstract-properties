
<!-- ======================================================================= -->
# Semantics of a graph

Without semantics, each graph is a meaningless set of tuples. And since graphs
are used to represent the relationships between "things", semantics are in
general implicitly associated with each graph. The following content attempts
to grasp the formal aspects related to the semantics of a graph.

<!-- ======================================================================= -->
## general considerations

The definition of a graph begins in general with a set of objects and the
relationships between them. These relationships can assumed to be defined
by semantical statements/expressions (e.g. `s := (x subcomponent-of y)`)
which, in the context of this discussion, are restricted to two arguments:
a 1st argument (e.g. `x`) and a 2nd argument (e.g. `y`).

In addition to that, and since the overall focus is on directed graphs, both
arguments are considered to be unequal. That is, **a level of significance**
can be assumed to exist over the arguments of a semantical expression - i.e.
one argument is considered super-ordinate to the other - e.g. a component is
considered to be more significant than its subcomponents.

A straight forward approach to define the semantics of a graph, while mapping
the agruments of an expression onto the vertices of an edge could be to map
the 1st argument of an expression to the 1st vertex of an edge, and the 2nd
argument to the 2nd vertex.

* e.g. `(s := (x subcomponent-of y)) => (e := (x,y))`.

Depending on the nature of an expression, this approach does however not
guarantee that the 1st vertex of an edge represents an object that is more
significant than the other. (Not that this would be a requirement). The
following considerations therefore focuses on two distinct orders:

1. The **index order** order of an edge: `(x presequent-to y)`.
   (i.e. Which argument is the 1st/source, and which the 2nd/sink vertex?).
2. The **order of significance** between both arguments: `(x subordinate-to y)`.
   (i.e. Which argument is semantically super-ordinate to the other?).

Put differently, the focus of this discussion is on "the order of vertices in
an edge" and "the order of significance between the arguments of an expression".

<!-- ======================================================================= -->
## semantical expressions

Generally speaking, an entity that has semantics can be understood to be
accompanied by a **semantical expression**, which defines the meaning of
an entity. Some mapping is therefore assumed to exist, that allows to
lookup the expression/semantics of each entity.

* `(sem: Entity -> Expression)`
* `sem(e)` returns the expression of entity `e`
* `sem(e)` may be defined as `sem(e) := <expression>`

A semantical expression is in general defined as a predicate. That is,
an expression is understood to return a single boolean value which is
true, if the expression applies to the given entity argument.

* `(s, expression: Entity -> Bool)`
* `s(e)` returns true, if the expression applies to entity `e`
* i.e. if `e` has the semantics expressed by the given statement

In the context of a relation `R`, the entities that can be associated
with a semantical expression, are its edges `(e in E)`:

For edge `e := (a,b)`, one might define `sem(e)` as:

* `a` is equal to `b`
* `a` is smaller than `b`
* `a` is subsequent to `b`
* `a` is an element of `b`
* `a` is a subset of `b`
* `a` is a multiple of `b`
* `b` is a multiple of `a`

Note that the latter two expressions are strictly speaking distinct from one
another since both build opon a different order of agruments. That is, the
order in which the arguments are taken from an edge, is relevant to a
semantical expression.

Note that the **characteristic function** of a relation `R()` can be used to
determine whether or not an edge exists that connects both of its arguments.
As such, `R()` allows to determine if both vertices are related with each
other. Because of that, `R()` can be understood to represent a mapping that
allows to lookup semantical expressions. However, since `R()` is only defined
to return a single boolean value, the actual meaning of `R()` must be known
in a given context - e.g. `R(a,b) := (a <= b)`.

Note that a graph, as a binary relation, can be understood to be accompanied by
a **vertex-to-object mapping** (i.e. `v(o)` and `o(v)`). As such, that mapping
can be understood to define the semantics of each vertex. That is because the
semantics of a vertex is to represent a specific object, the focus of this
discussion is therefore on the semantics of the edges in a graph.
