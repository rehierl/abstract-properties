
As was shown in previous chapters, several different encodings are possible.
Furthermore, the implementation of each encoding greatly depends on the tree
traversal algorithm that was used to produce a specific encoding. And finally,
several variations are possible when implementing an encoding.

Due to the amount of available options, which can not all be covered, it is
essential to understand the core concept behind each encoding. The following
will therefore **focus on** the pre-order versions of the level-based and the
length-based encodings in an attempt to recap the most important aspects of
both encodings.

Note that, from this point forward, the **pre-order** traversal will be assumed
as the default traversal algorithm. Hence, this particular tree traversal will
be mentioned explicitly only for clarification purposes.

Note that the intent behind these restricitions is to simplify discussions by
reducing the amount of variations one needs to keep in mind.
