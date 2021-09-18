
- type-x scope of a node
- type-0 - null scope vs. non-null scopes

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
