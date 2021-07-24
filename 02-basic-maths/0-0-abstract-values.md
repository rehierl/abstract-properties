
# abstract values

In the context of this dicussion, the smallest indivisible units are bits of
information which will be referred to as **(abstract) values**, **objects**,
**vertices** or **nodes**. Each such value may refer to an entity that is
simple or complex in nature. The exact nature of such a value is however not
relevant to this discussion. Based on that, these kind of abstract values
will be referred to as **atomic/primitive values**.

Similar to the above concept is our decimal numeral system, which uses symbols
such as the decimal digits (0 to 9), a decimal mark (.) and the minus sign (-).
These symbols are used to compose numerals, each of which represents a unique
abstract numeric value.

* e.g. The string of symbols "2.0" represents the abstract number 2.

Each abstract value is considered unique and therefore distinct to every other
value. Furthermore, the amount of values is considered to be **finite**. That
is, a set of abstract values is considered to be **countable**, which is why
each value can be understood to be associated with a unique natural number
(i.e. an identifier, in short an **id**). Atomic values are therefore
considered identifiable by their numeric id. Because of that, the numeric id of
a value will be used simlar to numerals, as the representative of such a value.

In order to refer to a particular abstract value of a given set of values, a
value's id will be prefixed with a letter/character (e.g. `v`) that is common
to all values in the corresponding set of values (e.g. `v3` or `v:3`); which
should help to avoid any confusion with actual number values.

* The value `v3` refers to the value that is associated with id `3`.
* e.g. The value `v3` refers to the abstract number `123`.

Note that, even though the relationship between a value and its id must in
general be considered **random**, the numeric ids themselves can still be
considered ordered according to the natural numbers. Because of that, the id
values can be seen as index values. However, and without further definition,
no order of any kind can be assumed in regards to the values themselves.

Note that the purpose of this concept of abstract values is to move past
thinking in terms of specific values; such as numbers or words. The reason
is that these are commonly associated with a "natrual order" of some sort
(e.g. ordered by numeric value, ordered alphabetically).

In order to allow statements about certain sets of values, numeral-based ids
can be generalized into letter-based ids. That is, single letters may be used
instead of concrete id values.

* `vi` is identified by `(i in [1,N])`
* `(v3 == v3)` and `(vi == vi)` are both always true
* `(vi == vj)` is true iff `(i == j)`, false otherwise
* iff := "if and only if"
