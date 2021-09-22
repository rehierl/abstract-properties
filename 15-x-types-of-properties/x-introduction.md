
<!-- ======================================================================= -->
## types of properties

```
... <n> c(n) </n> s(n) </p> s(p) ... </r>
|-t(T)--------------------------------->| - enter/exit the document
t0  |-|                                   - enter/visit/exit the node
t1  |-(scope)-->|                         - exit its (type-1) scope
t2  |-(extended scope)--->|               - a type-2 exit
t3  |-(unrestricted scope)------------->| - a type-3 exit
```

One can assume that there are four generic types of properties, each of which
is defined based upon the corresponding scope of its defining node. Because of
that, a type-x property can be understood to be defined such that its scope is
the type-x scope of its defining node.

* type-x property <=> type-x scope

Note that these scopes need to be seen as "default scopes". That is, depending
on a given context (e.g. rank values) it may or may not be possible to restrict
a property's scope to a prefix of its default scope.
