
# the end-based encoding (END)

The following focusses on howto implement and end-based encoding such that the
traversal algorithms output the index of the first/last node of the current
node's trace.

Note that this encoding scheme will be referred to as
**the end-based implicit encoding scheme**.

Recall that the pre-order trace of each node is a substring to the traces of its
ancestors. One might therefore suspect that the process of having to explicitly
count the nodes in a trace can be omitted. After all, the length of a trace can
be determined based on the index of its first and the index of its last node.

* `length = (last - first + 1)`

This change however only seems to have a noticeable effect on the encoding
algorithms. The decoding algorithms mostly remain as they are.
