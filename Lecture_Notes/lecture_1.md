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

