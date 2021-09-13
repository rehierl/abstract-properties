
- as a readme?

<!-- ======================================================================= -->
## scopes of properties

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-| type-0                                    t0[n]
t1-scope(n)            |-type-1--------|                             t1/U[n]
t2-scope(n)            |-type-2-------------------------|            t2/O[n]
t3-scope(n)            |-type-3--------------------------- ... -|    t3[n]
```

As mentioned before, properties in the context of this discussion are used
to mark/tag the nodes within a scope. That is, each property can be said to
be associated with a scope of one of the above types. Based on that, one can
in general speak of **a type-x property**, if the property's scope is of the
appropriate type. Likewise, each scope can be said to be associated with an
implicit property of the same type. Based on that, and depending on ones
focus, one can speak of "a property's scope" and/or of "a scope's property".

* type-x property <=> type-x scope

Note that each node can be understood to be located within more than one
scope. Because of that, **hierarchies of scopes** are formed based on the
nodes the scopes have in common (e.g. subset-of, substring-of).

Note that the above scopes need to be seen as **default scopes**. That is,
in a given context (e.g. rank values) it may be allowed to **restrict** the
scope of a property to a proper prefix of the property's default scope.

Note that a property's value is in general secondary in the context of this
discussion. As a matter of simplification, one can think of a property to
hold some unique reference as its value (e.g. a specific color).
