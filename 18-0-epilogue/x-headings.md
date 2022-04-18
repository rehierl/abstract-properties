
- which nodes are in the section of a heading?

<!-- ======================================================================= -->

```html
.. <div> .. <hA> heading </hA> contents </div> ..
   |<-----------------------------------| associate? - NO!
```

- `<div>` is presequent to `<hA>`
- the `div` container is no node in section `hA`
- it is an error to associate the `div` element with heading `hA`
- it is an error to associate any ancestor with the property of a descendant
- regardless of when exactly one would want to establish the association

Recall that no node above-of a heading belongs to the section of a heading.
Because of that, no node can count towards the section of a heading, if the
heading is subsequent to it in the document order.

Since the document order is order preserving in regards to DTU and DTO, the
same applies to the presequent siblings (including their descendants) of a
heading, the heading's ancestors, and also to the presequet siblings of any
such ancestor (including their descendants). None of these elements are
defined to be elements in the section of such a heading.

Conversely, the subsequent siblings of a heading (including their descendants),
the subsequent siblings of the heading's ancestors (including their descendants)
are subsequent to that heading in the document tree's pre-order trace. Because
of that, all of these nodes may in general belong to the section of a heading.

However, the document order does by itself not allow to conclude, if a specific
node that is subsequent to a heading is indeed a content node in the section of
a heading. Further clarifications are required.
