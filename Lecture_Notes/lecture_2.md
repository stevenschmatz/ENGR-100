# Lecture 2

Definition of engineering:

> Someone who applies scientific and mathematical principles to practical ends such as the design, manufacture, test, and operation of efficient and economical structures, machines, processes, and systems.

Definition of computer engineering:

> The design and low-level use of computers, which includes:
> * VLSI
> * Computer Architecture
> * Embedded Systems
> * System Software

### A little bit more on binary

Binary numbers can be unsigned or signed. Without prior knowledge of the signedness of the number, you can have no idea what the number actually is.

For example, 1100 could either be 12, if unsigned, or -4, if signed.

Note that with a signed number, you cannot express a number higher than \\(2^{b} - 1\\), where \\(b\\) is the number of bits of the number. Hence, you can't express a 4-bit signed number higher than 8.

### Truth tables

When a small number of outputs, it is a very powerful and useful tool. However, the number of rows increases exponentially:

$$\text{rows}(n) = 2^n$$

Hence, for 30 rows, there are around a billion entries.

## Digital Logic and Computers