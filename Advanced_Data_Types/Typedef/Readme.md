### Typedef
The ```typedef``` keyword is used to create new names(aliases) for existing data types. This can help make the code more readable, easier to understand, and easier to manage. The syntax for ```typedef```:
```
typedef existing_type new_name;
```
#### Define a new name for a basic data type
```
typedef unsigned int uint;

uint age = 25;  // uint is now a new name for unsigned int
```
#### Define a new name for a structure
```
typedef struct {
    int x;
    int y;
} Point;

Point p1;  // Point is now a new name for the struct containing x and y
p1.x = 10;
p1.y = 20;
```
#### Define a new name for a pointer
```
typedef char* string;

string name = "Alice";  // string is now a new name for char*
```
#### Define a new name for an enumeration (enum)
```
typedef enum {
    RED,
    GREEN,
    BLUE
} Color;

Color favoriteColor = BLUE;  // Color is now a new name for the enum containing the colors
```
#### Define a new name for an array
```
typedef int Array[10];

Array numbers;  // Array is now a new name for an array of 10 integers
```
