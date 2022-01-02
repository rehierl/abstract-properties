
<!-- ======================================================================= -->
# A pre-order end-based encoding

Since the pre-order trace of each node is a substring to the traces of its
ancestors, one might suspect that the process of having to explicitly count
the nodes in a trace can be omitted. After all, the length of a trace can
be determined based on the index of its first and the index of its last node.

* length = (last - first + 1)

This change however only seems to have a noticeable effect on the encoding
algorithms. The decoding algorithms mostly remain as they are.
