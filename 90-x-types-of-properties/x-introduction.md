
<!-- ======================================================================= -->
## types of properties

```
<r> .. <p> fs .. ps .. <n> fc .. lc .. </n> ns .. ls .. </p> .. </r>
====================================================================
t0-scope(n)            |-| type-0                                    | t0[n]
t1-scope(n)            |-type-1--------|                             | t1/U[n]
t2-scope(n)            |-type-2-------------------------|            | t2/O[n]
t3-scope(n)            |-type-3--------------------------- ... -|    | t3[n]
```

Due to the stream-based perspective on a property, the scope of a property can
only be defined as one of the scopes of its defining node. However, and since
a node may in general have any number of descendants, implementations still
have the issue of having to determine where in the pre-order trace of a tree
such a well-defined scope ends.

Despite the implementation-specific difficulties, one can however assume that
there are four generic types of properties, each of which is defined based
upon the corresponding scope of its defining node. Because of that, a **type-x
property** can be understood to be defined such that its scope is the type-x
scope of its defining node.

* type-x property <=> type-x scope

Note that these scopes need to be seen as "default scopes". That is, depending
on a given context (e.g. rank values) it may or may not be possible to restrict
a property's scope to a prefix of its default scope.
