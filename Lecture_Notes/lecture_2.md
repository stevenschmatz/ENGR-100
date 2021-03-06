# Lecture 2: Combinatorial Logic

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

## Verilog

Verilog is a hardware description language (HDL) that we use in ENGR 100-250. It looks a lot like C, but it is *not a programming language*. Why not? In an HDL, an OR-gate is OR-ing at all times. That's what it does. Whereas if you have a line of code, `A++`, it is only executed when you tell it to.

You need to think of an HDL as hardware, because that's really what it is.

### Gates in Verilog

A NOT gate can be done simply in a lot of ways. Here's an example how. Verilog doesn't do really well with creating simple gates, but you can do complex things easily.

```verilog
module NOT(
    input wire A,
    output reg B);
    
    always @* begin // constantly re-evaluate – combinatorial logic follows
        case (A)
            1'b0: begin // begin is same as {
                B = 1'b1; // 1 in binary
            end // and end is same as }
            
            1'b1: begin
                B = 1'b0; // 0 in binary
            end
        endcase
    end
endmodule
```

### Numbers in Verilog

* When describing a number, the first number describes how many bits the number is. 
* The tick tells that you're done describing that.
* The letter is the base of the number.
    * `b` is binary
    * `h` is hexadecimal
    * `d` is decimal
* The last number is the number, in whatever base system you're using.

### Miscellaneous Verilog things

##### Only the value at the end matters.
You can switch all the variables all the time in a loop, but the hardware will only build the final value. We're just implementing a truth table. Verilog code actually gets converted into a truth table (or logic that implements a truth table).

##### If a value is assigned in an `always` block, it should be a reg. Otherwise, it should be a wire.

It's syntactic annoyance, but it is what it is. There's no deep knowledge behind it.

##### If it feels verbose, that's fine.

Verilog is suboptimal for simple gates, but greatly simplifies creation of large truth tables (an 8-input module would otherwise have 256 cases)!

#### Some more symbols
Familiar symbols:
* `&&` is AND
* `||` is OR
* `!` is NOT
* `==, !=, >, >=` for comparison
* `^` is XOR.
* `+, -, *` for arithmetic.
* Numbers are unsigned where it matters.

#### Example – Four 4-bit adder

This would be a lot more complicated in a truth table (it would have 256 rows!)

```verilog
module add(
    input wire[3:0] in1,
    input wire[3:0] in2,
    output reg[4:0] out);
    
    always @* begin
        out[4:0] = in1[3:0] + in2[3:0];
    end
endmodule
```

Instead, you could list out a bunch of `if`-statements covering all possible cases. That would give the exact same answer. This is just a simplified version.

## Review
* **Combinatorial logic**: Logic with no memory. There is no stored information.
* **Register**: A place that stores information
* **Bus**: A group of wires.

## Another Example

This is meant to compute \\(AB + CD\\):

```verilog
module mult(
    input wire [3:0] in1,
    input wire [3:0] in2,
    output reg [3:0] out);
    
    always @* begin
        out = in1 * in2;
    end
endmodule

module add(
    input wire [3:0] in1,
    input wire [3:0] in2,
    output reg [3:0] out);
    
    always @* begin
        out = in1 + in2;
    end
endmodule

module top(
    input wire [3:0] A,
    input wire [3:0] B,
    input wire [3:0] C,
    input wire [3:0] D,
    output wire [3:0] result);
    
    always @* begin
        wire [3:0] tmp1;
        wire [3:0] tmp2;
        
        mult u1(A, B, tmp1); // module instantiation
        mult u2(A, B, tmp2); // again
        add u3(tmp1, tmp2, result);
    end
endmodule
```

Note that you could actually define this in any order! You're just describing hardware, so it doesn't matter.












