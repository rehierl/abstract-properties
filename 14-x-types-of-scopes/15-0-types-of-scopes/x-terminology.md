
the extension of scopes
- type-0 is "only the node"
- type-1 is "the scope of a node"
- all descendants in the unordered doctree
- type-2 is "the extended scope of a node"
- all descendants in the ordered doctree
- its descendants + siblings and their descendants
- show - a sequence of units - induced subtrees
- similar boxing issues with "distant descendants"
- restricted by the scope of their parent
- type-3 is "the unrestricted scope of a node"
- until the very end of a document

clarifications
- "enter a node" - enter t0, t1, t2, t3
- "exit a node" - "exit t0" (only)
- "visit a node" - enter t0 until exit t0
- enter/exit the scope of a node - enter/exit t1

recall html-elements
- enter - process an element's start-tag
- enter all of its scopes in one go
- exit - process an element's end-tag
- exit t0 - exit the start-tag
- exit t1 - exit the node's end-tag
- exit t2 - exit the parent's end-tag
- exit t3 - exit the root's end-tag

<!-- ======================================================================= -->
## remarks

Note that future extensions, such as rank values, may in principle close a
scope before the corresponding end-tag is reached. Based on that, one can speak
of **default scopes**. Implementations must therefore take into account that a
close operation will be triggered repeatedly.
