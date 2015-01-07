# Introduction to Digital Logic

In digital logic, variables can either be true (**T**) or false (**F**).

## Operators

In the English language, `or` is ambiguous: exclusive or, and inclusive or:

* `and`
:   Only true if both are true.
* `or` (inclusive)
:   "If you tell Jeff or James, that's fine."
* `xor` (exclusive)
:   "Either tell Jeff or James, but not both."
* `not`
:   False becomes true, and true becomes false.

## Representation of Boolean Logic

Boolean logic can be represented in circuits, with a high voltage representing **T** values and low voltages representing **F** values. 

ANDs, ORs, and NOTs are logically complete. Hence, you can represent any Boolean function as a combination of these gates.

|Operation  | Electrical/Computer Engineering   | Gate
|---        |                               --- |        ---|
| Y and Z   |\\(Y \cdot Z\\)                    |![AND](http://i.imgur.com/V0Eip7Z.png)|
| Y or Z    |\\(Y + Z\\)                        |![OR](http://i.imgur.com/c339pnu.png)           |
| not Y     |\\(\bar{Y}\\)                      |![NOT](http://i.imgur.com/ytlsb1y.png)|
| Y xor Z   |\\(Y \oplus Z\\)                   |![XOR](http://i.imgur.com/7TSHPqy.png)|

## Alternative Number Systems

Numbers in other bases always follow the following pattern: the value of each place value is \\(x * b^n\\), where \\(x\\) is the number at the place value, \\(b\\) is the base, and \\(n\\) is the significance of the digit (starting from 0 on the least significant digit). The value of the number is just the sum of the place values.

Hence, 101 in base 2 (binary) is:

$$(1 * 2^2) + (0 * 2^1) + (1 * 2^0) = 4 + 0 + 1 = 5$$

And 824 in base 6 is:
$$(8 * 6^2) + (2 * 6^1) + (4 * 6^0) = 304$$

## Binary Addition

Addition in binary is done the same way addition is done in base 10: you add each digit separately, starting from the least significant digit, and you carry over values if you need to:

$$101 + 110 = 1011$$

Consider the case of adding two one-digit binary numbers. The result of the binary addition could be anywhere between \\(0\\) (0) and \\(10\\) (2), depending on the values of your operands \\(A\\) and \\(B\\). Hence, you can keep track of each digit you get after doing the addition:

$$A + B = R _1 R _2$$

where \\(R_1\\) and \\(R _2\\) are digits. Hence,

|A  |B  |\\(R_1\\)  |\\(R _2\\) |
|---|---|---        |---        |
|0|0|0|0|
|0|1|0|1|
|1|0|0|1|
|1|1|1|0|

Notice how \\(R_1\\) is essentially the `and` function on \\(A\\) and \\(B\\), and \\(R _2\\) is the `xor` function on \\(A\\) and \\(B\\). Therefore, a logical circuit can be constructed to do this addition!

![Adder](http://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Half_Adder.svg/180px-Half_Adder.svg.png)





