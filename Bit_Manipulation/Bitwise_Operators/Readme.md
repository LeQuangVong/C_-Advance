Bitwise operators are used in programming to perform operations on binary numbers at the bit level. These operators are called bitwise because they operate on each individual bit of the operands. Unlike logical operators (such as ```&&``` and ```||``` in many languages) that operate on entire Boolean values, bitwise operators work directly on the binary representation of numbers.

#### Common Bitwise Operators
##### AND (&):

- Operation: Compares (so sánh) each bit of two operands (toán hạng). If both corresponding bits are ```1```, the resulting bit is ```1```. Otherwise, the resulting bit is ```0```.
- Example:
```
a = 5      # 0101 in binary
b = 3      # 0011 in binary
result = a & b   # 0001 in binary, which is 1 in decimal
```

##### OR (|):

- Operation: Compares each bit of two operands. If at least one of the corresponding bits is ```1```, the resulting bit is ```1```. Otherwise, the resulting bit is ```0```.
- Example:
```
a = 5      # 0101 in binary
b = 3      # 0011 in binary
result = a | b   # 0111 in binary, which is 7 in decimal
```

##### XOR (^):

- Operation: Compares each bit of two operands. If the corresponding bits are different, the resulting bit is ```1```. If they are the same, the resulting bit is ```0```.
- Example:
```
a = 5      # 0101 in binary
b = 3      # 0011 in binary
result = a ^ b   # 0110 in binary, which is 6 in decimal
```

##### NOT (~):

- Operation: Flips all the bits of the operand. All ```1``` bits become ```0```, and all ```0``` bits become ```1```.
- Example:
```
a = 5      # 0101 in binary
result = ~a   # 1010 in binary, which is -6 in decimal (two's complement representation)
```

##### Left Shift (<<):

- Operation: Shifts the bits of the operand to the left by the specified number of positions. Zeros are added on the right side.
- Example:
```
a = 5      # 0101 in binary
result = a << 1   # 1010 in binary, which is 10 in decimal
```

##### Right Shift (>>):

- Operation: Shifts the bits of the operand to the right by the specified number of positions. The sign bit (for signed integers) is preserved.
- Example:
```
a = 5      # 0101 in binary
result = a >> 1   # 0010 in binary, which is 2 in decimal
```
#### Differences Between Bitwise and Logical Operators
- Bitwise Operators: Operate on the individual bits of integer operands.
- Logical Operators: Operate on entire Boolean expressions, producing a true or false value based on the overall condition.
