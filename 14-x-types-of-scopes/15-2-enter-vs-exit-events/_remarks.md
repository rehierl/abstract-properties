
- point out implementation-specific aspects
- howto actually detect the end of a scope

dom tree - order embedding
- point out the implementation-specific
  aspects of a dom tree
- explain why the tree orders can still be said
  to be a suborders to that non-tree graph

the overall issue
- implementations create objects that must be maintained
- objects don't update themselves when exiting a scope
- implementations must update objects explicitly
- how one could implement the support of types of scopes
- this is the default - extensions must be implemented accordingly

<!-- ======================================================================= -->
## remarks

Note that, in addition to obvious input errors, production code will have to
take into account that a root could be misused to declare a type-2/3 property.
In such cases, these property definitions must be ignored.

Note that, depending on property definitions, a specific **closing order** may
be required. That is because a descendant scope/section will in general have
to be closed before its ancestor scopes (i.e. in case of a section hierarchy).
The above algorithm does obviously not take such a closing order into account.
