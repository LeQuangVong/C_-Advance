A bitmask is a sequence of bits (binary digits) that can be used to manipulate specific bits within a binary number. Bitmasks are particularly useful for tasks that involve checking, setting, clearing, or toggling individual bits in a data structure, such as managing flags, permissions, or statuses.

#### Basic Operations with Bitmasks
Common operations performed using bitmasks include:
- Setting a bit: Turn on a specific bit.
- Clearing a bit: Turn off a specific bit.
- Toggling a bit: Switch the bit from ```0``` to ```1``` or from ```1``` to ```0```.
- Checking a bit: Determine if a specific bit is set ```1``` or not ```0```.

##### Setting a Bit
To set a specific bit to ```1```, use the bitwise ```OR (|)``` operator with a mask where only the desired bit is set to ```1```.
```
int number = 0b0010; // Binary: 0010
int mask = 0b0100;   // Binary: 0100

number |= mask;      // Result: 0110 (binary), 6 (decimal)
```

##### Clearing a Bit
To clear a specific bit (set it to ```0```), use the bitwise ```AND (&)``` operator with the complement ```(~)``` of the mask.
```
int number = 0b0110; // Binary: 0110
int mask = 0b0010;   // Binary: 0010

number &= ~mask;     // Result: 0100 (binary), 4 
(decimal)
```
##### Toggling a Bit
To toggle a bit (flip its value), use the bitwise ```XOR (^)``` operator with a mask.
```
int number = 0b0101; // Binary: 0101
int mask = 0b0010;   // Binary: 0010

number ^= mask;      // Result: 0111 (binary), 7 (decimal)
```
##### Checking a Bit
To check if a specific bit is set, use the bitwise ```AND (&)``` operator with a mask. The result is non-zero if the bit is set.
```
int number = 0b0110; // Binary: 0110
int mask = 0b0010;   // Binary: 0010

bool isSet = (number & mask) != 0; // True (the bit is set)
```
#### Example
Managing User Permissions: 
Imagine a system where a user can have different permissions: Read, Write, and Execute.

- Read: 1st bit (0b001)
- Write: 2nd bit (0b010)
- Execute: 3rd bit (0b100)
```
int permissions = 0b000; // No permissions

// Grant read and write permissions
permissions |= 0b001; // Grant Read
permissions |= 0b010; // Grant Write

// Check if the user has write permission
bool canWrite = (permissions & 0b010) != 0; // True

// Revoke write permission
permissions &= ~0b010; // Remove Write
```
