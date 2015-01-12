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

Note that with a signed number, you cannot express a number higher than \\(2^{b-1} - 1\\), where \\(b\\) is the number of bits of the number. Hence, you can't express a 4-bit signed number higher than 8.

### Truth tables

When a small number of outputs, it is a very powerful and useful tool. However, the number of rows increases exponentially:

$$\text{rows}(n) = 2^n$$

Hence, for 30 rows, there are around a billion entries.

## Digital Logic and Computers

Digital circuits work by representing a high voltage as a 1, and a low voltage as a 0.

Digital circuits manipulate bits. We can do this with AND, OR, etc. gates to compute values. Other things you can do with bits are:
* Group them. Note: A "word" is a group of bits of standard length.
* Move them. This is done over a wire. An array of wires is a bus (see below).
* Store them, in *registers.*

### Buses

A group of wires as input to a digital circuit is known as a *bus*.

In Verilog, a group of 7 wires is denoted as:

```
A[6,0]
```

So... *why does this go from big to small*? Because "I like it that way."

**Endian-ness**: Do we go from big to small or small to big?
* A reference from Gulliver's travels, and it's completely arbitrary.

**Register**: A place to store a bit.

### Schematic representation

We can represent a logical function with input and output as a blob, with inputs as wires pointing in and outputs pointing out. In math, a function with input of \\(A\\) and output of \\(B\\) is represented by:

$$B = f(A)$$

Unlike in a mathematical function, a logical function has a time delay. This is known as a *propagation delay*.

If the output depends only on the current combination of inputs, it is known as a *combinational logic*. With a truth table, you can specify how a combinatoric function works without knowing how. 

### Verilog

Verilog is a hardware description language (HDL) that we use in ENGR 100-250. It looks a lot like C, but it is *not a programming language*. Why not? In an HDL, an OR-gate is OR-ing at all times. That's what it does. Whereas if you have a line of code, `A++`, it is only executed when you tell it to.

You need to think of an HDL as hardware, because that's really what it is.

A NOT gate can be done simply in a lot of ways. Here's an example how. Verilog doesn't do really well with creating simple gates, but you can do complex things easy.

```verilog
module NOT(
    input wire A,
    output reg B);
    
    always @* begin
        case (A)
            1'b0: begin
                B = 1'b1;
            end
            
            1'b1: begin
                B = 1'b0;
            end
        endcase
    end
endmodule
```

