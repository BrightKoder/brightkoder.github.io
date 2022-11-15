## Data Types

All variables use data-type during declaration to restrict the type of data to be stored. Therefore, we can say that data types are used to tell the variables the type of data it can store. Whenever a variable is defined in C++, the compiler allocates some memory for that variable based on the data type with which it is declared. Every data type requires a different amount of memory.

C++ supports a wide variety of data types and the programmer can select the data type appropriate to the needs of the application. Data types specify the size and types of value to be stored. However, storage representation and machine instructions to manipulate each data type differ from machine to machine, although C++ instructions are identical on all machines.

C++ supports the following data types:

+ Primary or Built in or Fundamental data type
+ Derived data types
+ User defined data types

![DatatypesInC](https://user-images.githubusercontent.com/83718460/201631087-c12fe5fc-7868-4ce4-be6e-dd799d6911a9.png)

### Primitive Data Types:

These data types are built-in or predefined data types and can be used directly by the user to declare variables. example: `int`, `char`, `float`, `bool`, etc. 
Primitive data types available in C++ are: 

##### Integer

+ The `int` keyword is used to indicate integers.
+ Its size is usually 4 bytes. Meaning, it can store values from -`2147483648` to `2147483647`.

```cpp
//For example,
int salary = 85000;
```
##### Floating Point Numbers
+ `float` and `double` are used to store floating-point numbers (decimals and exponentials).
+ The size of `float` is 4 bytes and the size of `double` is 8 bytes. Hence, `double` has two times the precision of `float`. 

```cpp
For example,
float area = 64.74;
double volume = 134.64534;
```
As mentioned above, these two data types are also used for exponentials. For example,

```cpp
double distance = 45E12    // 45E12 is equal to 45*10^12
```

##### Character
+ Keyword `char` is used for characters.
+ Its size is 1 byte.
+ Characters in C++ are enclosed inside single quotes ' '.

```cpp
//For example,
char test = 'h';

char ch = 65; // ASCII value of A (integer value can be stored in charactor type variable)

```

##### Wide Character
+ Wide character `wchar_t` is similar to the `char` data type, except its size is 2 bytes instead of 1.
+ It is used to represent characters that require more memory to represent them than a single `char`.

```cpp
//For example,
wchar_t test = L'ם'  // storing Hebrew character;
```

Notice the letter L before the quotation marks.

---

> Note: There are also two other fixed-size character types `char16_t` and `char32_t` introduced in C++11.

---

##### Boolean

+ The bool data type has one of two possible values: `true` or `false`.
+ Booleans are used in conditional statements and loops (which we will learn in later chapters).

```cpp
For example,
bool cond = false;
```

##### Valueless or Void
+ The `void` keyword indicates an absence of data. It means "nothing" or "no value".
+ We will use `void` when we learn about functions and pointers.

---
> Note: We cannot declare variables of the `void` type.

---

#### C++ Type Modifiers
We can further modify some of the fundamental data types by using type modifiers. There are 4 type modifiers in C++. 

They are:

1. `signed`
2. `unsigned`
3. `short`
4. `long`

We can modify the following data types with the above modifiers:

+ `int`
+ `double`
+ `char`

#### C++ Modified Data Types List
| Data Type           | Size (in Bytes) | Meaning                                                                           |
|:--------------------|:---------------:|:----------------------------------------------------------------------------------|
| signed int	      | 4	            | used for integers (equivalent to int)                                             |
| unsigned int	      | 4	            | can only store positive integers                                                  |
| short	              | 2	            | used for small integers (range -32768 to 32767)                                   |
| unsigned short      | 2	            | used for small positive integers (range 0 to 65,535)                              |
| long	at least      | 4	            | used for large integers (equivalent to long int)                                  |
| unsigned long       | 4               |  used for large positive integers or 0 (equivalent to unsigned long int)          |
| long long           | 8	            | used for very large integers (equivalent to long long int).                       |
| unsigned long long  | 8	            | used for very large positive integers or 0 (equivalent to unsigned long long int) |
| long double	      | 12	            | used for large floating-point numbers                                             |
| signed char	      | 1	            | used for characters (guaranteed range -127 to 127)                                |
| unsigned char	      | 1	            | used for characters (range 0 to 255)                                              |


###### Examples

```cpp
long b = 4523232;
long int c = 2345342;
long double d = 233434.56343;
short d = 3434233; // Error! out of range
unsigned int a = -5;    // Error! can only store positive numbers or 0
```

### Derived Data Types: 

The data types that are derived from the primitive or built-in datatypes are referred to as Derived Data Types. These can be of four types namely: 

+ Function
+ Array
+ Pointer
+ Reference

We will learn about these derived data types in later tutorials.

### Abstract or User-Defined Data Types: 

These data types are defined by the user itself. Like, as defining a class in C++ or a structure. 
C++ provides the following user-defined datatypes: 

1. Class
2. Structure
3. Union
4. Enumeration
5. Typedef defined Datatype

We will learn about these User-Defined data types in later tutorials.

## Type Conversions

C++ allows us to convert data of one type to that of another. This is known as type conversion.

There are two types of type conversion in C++.

1. Implicit Conversion
2. Explicit Conversion (also known as Type Casting)


#### Implicit Type Conversion
The type conversion that is done automatically done by the compiler is known as implicit type conversion. This type of conversion is also known as automatic conversion.

Let us look at two examples of implicit type conversion.

###### Example 1: Conversion From int to double

```cpp
// Working of implicit type-conversion

#include <iostream>
using namespace std;

int main() {
   // assigning an int value to num_int
   int num_int = 9;

   // declaring a double type variable
   double num_double;
 
   // implicit conversion
   // assigning int value to a double variable
   num_double = num_int;

   cout << "num_int = " << num_int << endl;
   cout << "num_double = " << num_double << endl;

   return 0;
}
```

###### Output

```sh
num_int = 9
num_double = 9

```

In the program, we have assigned an `int` data to a `double` variable.

```cpp
num_double = num_int;

```

Here, the `int` value is automatically converted to `double` by the compiler before it is assigned to the `num_double` variable. This is an example of implicit type conversion.

###### Example 2: Automatic Conversion from double to int

```cpp
//Working of Implicit type-conversion

#include <iostream>
using namespace std;

int main() {

   int num_int;
   double num_double = 9.99;

   // implicit conversion
   // assigning a double value to an int variable
   num_int = num_double;

   cout << "num_int = " << num_int << endl;
   cout << "num_double = " << num_double << endl;

   return 0;
}
```

###### Output
```sh
num_int = 9
num_double = 9.99
```

In the program, we have assigned a `double` data to an `int` variable.

```cpp
num_int = num_double;
```

Here, the `double` value is automatically converted to `int` by the compiler before it is assigned to the `num_int` variable. This is also an example of implicit type conversion.

---
> **Note:** Since int cannot have a decimal part, the digits after the decimal point are truncated in the above example.
>
---

#### Data Loss During Conversion (Narrowing Conversion)
As we have seen from the above example, conversion from one data type to another is prone to data loss. This happens when data of a larger type is converted to data of a smaller type.
  
  ![cpp-type-conversion](https://user-images.githubusercontent.com/83718460/201832575-2ec08c6d-71b4-4bb1-baad-ebd3e04f9566.png)



#### C++ Explicit Conversion
When the user manually changes data from one type to another, this is known as explicit conversion. This type of conversion is also known as type casting.

There are three major ways in which we can use explicit conversion in C++. They are:

1. C-style type casting (also known as cast notation)
2. Function notation (also known as old C++ style type casting)
3. Type conversion operators

##### C-style Type Casting
As the name suggests, this type of casting is favored by the C programming language. It is also known as cast notation.

The syntax for this style is:
```cpp
(data_type)expression;
```

##### Function-style Casting
We can also use the function like notation to cast data from one type to another.

The syntax for this style is:

```cpp
data_type(expression);
```

###### Example 3: Type Casting

```cpp
#include <iostream>

using namespace std;

int main() {
    // initializing a double variable
    double num_double = 3.56;
    cout << "num_double = " << num_double << endl;

    // C-style conversion from double to int
    int num_int1 = (int)num_double;
    cout << "num_int1   = " << num_int1 << endl;

    // function-style conversion from double to int
    int num_int2 = int(num_double);
    cout << "num_int2   = " << num_int2 << endl;

    return 0;
}
```
###### Output
```sh
num_double = 3.56
num_int1   = 3
num_int2   = 3
```

---

<style>
.my-ft-link:link, .my-ft-link:visited {
  background-color: white;
  color: black;
  border: 2px solid green;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
}

.my-ft-link:hover, .my-ft-link:active {
  background-color: green;
  color: white;
}
  
.my-footer {
  text-align: center;
}

.my-footer1 {
  text-align: left;
  display:inline;
}

.my-footer2 {
  text-align: right;
  display:inline;
}
</style>

<div class="my-footer">
  <div class="my-footer1">
    <a href="./a_intro.html" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="./c_basic_input_output.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---
