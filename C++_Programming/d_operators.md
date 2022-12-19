## Operators

In this tutorial, we will learn about the different types of operators in C++ with the help of examples. In programming, an operator is a symbol that operates on a value or a variable.

Operators are symbols that perform operations on variables and values. For example, `+` is an operator used for addition, while `-` is an operator used for subtraction.

Operators in C++ can be classified into 6 types:

1. [Arithmetic Operators](#Arithmatic-Operators)
2. [Assignment Operators](#Assignment-Operators)
3. [Relational Operators](#Relational-Operators)
4. [Logical Operators](#Logical-Operators)
5. [Bitwise Operators](#Bitwise-Operators)
6. [Other Operators](#Other-Operators)

### Arithmatic Operators {#Arithmatic-Operators}

Arithmetic operators are used to perform arithmetic operations on variables and data. 

For example,

```
a+b
```

Here, the `+` operator is used to add two variables a and b. Similarly there are various other arithmetic operators in C++.


| Operator	| Operation
|:---------:|:----------------------------------------------|
|   +	    | Addition                                      |
|   -	    | Subtraction                                   |
|   *	    | Multiplication                                |
|   /       | Division                                      |
|   %	    | Modulo Operation (Remainder after division)   |

###### Example: Arithmetic Operators
```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    a = 7;
    b = 2;

    // printing the sum of a and b
    cout << "a + b = " << (a + b) << endl;

    // printing the difference of a and b
    cout << "a - b = " << (a - b) << endl;

    // printing the product of a and b
    cout << "a * b = " << (a * b) << endl;

    // printing the division of a by b
    cout << "a / b = " << (a / b) << endl;

    // printing the modulo of a by b
    cout << "a % b = " << (a % b) << endl;

    return 0;
}
```

###### Output

```
a + b = 9
a - b = 5
a * b = 14
a / b = 3
a % b = 1
```

Here, the operators `+`, `-` and `*` compute addition, subtraction, and multiplication respectively.

Note the operation `(a / b)` in our program. The `/` operator is the division operator.

As we can see from the above example, if an integer is divided by another integer, we will get the quotient. However, if either divisor or dividend is a floating-point number, we will get the result in decimals.

```cpp
7/2 is 3
7.0 / 2 is 3.5
7 / 2.0 is 3.5
7.0 / 2.0 is 3.5
```

The modulo operator `%` computes the remainder. When `a = 9` is divided by `b = 4`, the remainder is `1`.

---

>
> **NOTE:** The % operator can only be used with integers.
>

---


#### Increment and Decrement Operators
C++ also provides increment and decrement operators: `++` and `--` respectively.

`++` increases the value of the operand by 1
`--` decreases it by 1

For example,

```cpp
int num = 5;

// increment operator
++num;  // 6
```

Here, the code `++num;` increases the value of num by 1.

###### Example: Increment and Decrement Operators

```cpp
// Working of increment and decrement operators

#include <iostream>
using namespace std;

int main() {
    int a = 10, b = 100, result_a, result_b;

    // incrementing a by 1 and storing the result in result_a
    result_a = ++a;
    cout << "result_a = " << result_a << endl;


    // decrementing b by 1 and storing the result in result_b   
    result_b = --b;
    cout << "result_b = " << result_b << endl;

    return 0;
}
```

###### Output
```sh
result_a = 11
result_b = 99
```
In the above program, we have used the `++` and `--` operators as prefixes (`++a` and `--b`). However, we can also use these operators as postfix (`a++` and `b--`).

###### Example:Increment and Decrement Operators

```cpp
#include <iostream>

using namespace std;

int main() {
   int var1 = 5, var2 = 5;

   // 5 is displayed
   // Then, var1 is increased to 6.
   cout << "var1 = " << var1++ << endl;

   // var2 is increased to 6
   // Then, it is displayed.
   cout << "var2 = " << ++var2 << endl;

   return 0;
}
```

###### Output

```sh
var1 = 5

var2 = 6
```

### C++ Assignment Operators {#Assignment-Operators}

In C++, assignment operators are used to assign values to variables. For example,

```cpp
// assign 5 to a
a = 5;
```

Here, we have assigned a value of `5` to the variable `a`.

| Operator     | Example	| Equivalent to   |
|:------------:|:----------:|:---------------:|
|   `=`	       |  `a = b;`	| `a = b;`        |
|   `+=`	   |  `a += b;`	| `a = a + b;`    |
|   `-=`	   |  `a -= b;`	| `a = a - b; `   |
|   `*=`       |  `a *= b;`	| `a = a * b;`    |
|   `/=`	   |  `a /= b;`	| `a = a / b;`    |
|   `%=`	   |  `a %= b;`	| `a = a % b;`    |

###### Example 3: Assignment Operators

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;

    // 2 is assigned to a
    a = 2;

    // 7 is assigned to b
    b = 7;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    cout << "\nAfter a += b;" << endl;

    // assigning the sum of a and b to a
    a += b;  // a = a +b
    cout << "a = " << a << endl;

    return 0;
}
```

###### Output

```sh
a = 2
b = 7

After a += b;
a = 9
```

#### Relational Operators {#Relational-Operators}

A relational operator is used to check the relationship between two operands. For example,

```cpp
// checks if a is greater than b
a > b;
```

Here, `>` is a relational operator. It checks if `a` is greater than `b` or not.

If the relation is **true**, it returns **1** whereas if the relation is **false**, it returns **0**.

| Operator | Meaning                     | Example                    |
|:--------:|:---------------------------:|:---------------------------|
| `==`	   | `Is Equal To`	             | `3 == 5 gives us false`    |
| `!=`	   | `Not Equal To`	             | `3 != 5 gives us true`     |
| `>`	   | `Greater Than`	             | `3 > 5 gives us false`     |
| `<`	   | `Less Than`	             | `3 < 5 gives us true`      |
| `>=`	   | `Greater Than or Equal To`  | `3 >= 5 give us false`     |
| `<=`	   | `Less Than or Equal To`	 | `3 <= 5 gives us true`     |

###### Example: Relational Operators

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    a = 3;
    b = 5;
    bool result;

    result = (a == b);   // false
    cout << "3 == 5 is " << result << endl;

    result = (a != b);  // true
    cout << "3 != 5 is " << result << endl;

    result = a > b;   // false
    cout << "3 > 5 is " << result << endl;

    result = a < b;   // true
    cout << "3 < 5 is " << result << endl;

    result = a >= b;  // false
    cout << "3 >= 5 is " << result << endl;

    result = a <= b;  // true
    cout << "3 <= 5 is " << result << endl;

    return 0;
}
```

###### Output
```sh
3 == 5 is 0
3 != 5 is 1
3 > 5 is 0
3 < 5 is 1
3 >= 5 is 0
3 <= 5 is 1
```

---

> **Note:** Relational operators are used in decision-making and loops.

---

#### Logical Operators {#Logical-Operators}

Logical operators are used to check whether an expression is `true` or `false`. If the expression is `true`, it returns `1` whereas if the expression is `false`, it returns `0`.

| Operator | Example	                    | Meaning                                                            |
|:--------:|:--------------------------:    |:-------------------------------------------------------------------|
| `&&`	   | `expression1 && expression2`	| `Logical AND. True only if all the operands are true.             `|
| `||`	   | `expression1 || expression2`	| `Logical OR. True if at least one of the operands is true.        `|
|  `!`	   | `!expression`                  | `Logical NOT. True only if the operand is false.                  `|

In `C++`, logical operators are commonly used in decision making. To further understand the logical operators, 

let's see the following examples,

```sh
Suppose,
a = 5
b = 8

Then,

(a > 3) && (b > 5) evaluates to true
(a > 3)  && (b < 5) evaluates to false

(a > 3) || (b > 5) evaluates to true
(a > 3) || (b < 5) evaluates to true
(a < 3) || (b < 5) evaluates to false

!(a < 3) evaluates to true
!(a > 3) evaluates to false
```

###### Example: Logical Operators

```cpp
#include <iostream>
using namespace std;

int main() {
    bool result;

    result = (3 != 5) && (3 < 5);     // true
    cout << "(3 != 5) && (3 < 5) is " << result << endl;

    result = (3 == 5) && (3 < 5);    // false
    cout << "(3 == 5) && (3 < 5) is " << result << endl;

    result = (3 == 5) && (3 > 5);    // false
    cout << "(3 == 5) && (3 > 5) is " << result << endl;

    result = (3 != 5) || (3 < 5);    // true
    cout << "(3 != 5) || (3 < 5) is " << result << endl;

    result = (3 != 5) || (3 > 5);    // true
    cout << "(3 != 5) || (3 > 5) is " << result << endl;

    result = (3 == 5) || (3 > 5);    // false
    cout << "(3 == 5) || (3 > 5) is " << result << endl;

    result = !(5 == 2);    // true
    cout << "!(5 == 2) is " << result << endl;

    result = !(5 == 5);    // false
    cout << "!(5 == 5) is " << result << endl;

    return 0;
}
```

###### Output

```sh
(3 != 5) && (3 < 5) is 1
(3 == 5) && (3 < 5) is 0
(3 == 5) && (3 > 5) is 0
(3 != 5) || (3 < 5) is 1
(3 != 5) || (3 > 5) is 1
(3 == 5) || (3 > 5) is 0
!(5 == 2) is 1
!(5 == 5) is 0
```

##### Explanation of logical operators with examples

+ `(3 != 5) && (3 < 5)` evaluates to `1` because both operands `(3 != 5)` and `(3 < 5)` are `1` (`true`).

+ `(3 == 5) && (3 < 5)` evaluates to `0` because the operand `(3 == 5)` is `0` (`false`).

+ `(3 == 5) && (3 > 5)` evaluates to `0` because both operands `(3 == 5)` and `(3 > 5)` are `0` (`false`).

+ `(3 != 5) || (3 < 5)` evaluates to `1` because both operands `(3 != 5)` and `(3 < 5)` are `1` (`true`).

+ `(3 != 5) || (3 > 5)` evaluates to `1` because the operand `(3 != 5)` is `1` (`true`).

+ `(3 == 5) || (3 > 5)` evaluates to `0` because both operands `(3 == 5)` and `(3 > 5)` are `0` (`false`).

+ `!(5 == 2) `evaluates to `1` because the operand (`5 == 2)` is `0` (`false`).

+ `!(5 == 5)` evaluates to `0` because the operand `(5 == 5)` is `1` (`true`).


### Bitwise Operators {#Bitwise-Operators}

In C++, bitwise operators perform operations on integer data at the individual bit-level. These operations include seting, clearing, toggling, shifting the actual bits. For example,

```cpp
a|b
a&b
a<<2
a^b
```

Here is a list of 6 bitwise operators included in C++.

| Operator    | Description                  |
|:-----------:|:-----------------------------|
| `&`         | Bitwise AND Operator         |
| `|`         | Bitwise OR Operator          |
| `^`         | Bitwise XOR Operator         |
| `~`         | Bitwise Complement Operator  |
| `<<`        | Bitwise Shift Left Operator  |
| `>>`        | Bitwise Shift Right Operator |


These operators are necessary because the Arithmetic-Logic Unit (ALU) present in the computer's CPU carries out arithmetic operations at the bit-level.


---

> **Note:** Bitwise operators can only be used alongside `char` and `int` data types.

---

#### 1. Bitwise AND Operator
The bitwise **AND** `&` operator returns **1** if and only if both the operands are **1**. Otherwise, it returns **0**.

The following table demonstrates the working of the bitwise **AND** operator. Let `a` and `b` be two operands that can only take binary values i.e. **1** and **0**.

| a  |  b | a & b |
|:--:|:--:|:-----:|
| 0  | 0  | 0     |
| 0  | 1  | 0     |
| 1  | 0  | 0     |
| 1  | 1  | 1     |

---
> **Note:** The table above is known as the "Truth Table" for the bitwise **AND** operator.

---

Let's take a look at the bitwise AND operation of two integers 12 and 25:

```cpp
12 = 00001100 (In Binary)

25 = 00011001 (In Binary)

//Bitwise AND Operation of 12 and 25

     00001100
&    00011001
     _________
     00001000  = 8 (In decimal)

```
###### Example: Bitwise AND
```cpp
#include <iostream>
using namespace std;

int main() {
    // declare variables
    int a = 12, b = 25;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    cout << "a & b = " << (a & b) << endl;

    return 0;
}
```

###### Output
```sh
a = 12
b = 25
a & b = 8
```
In the above example, we have declared two variables `a` and `b`. Here, notice the line,

```cpp
cout << "a & b = " << (a & b) << endl;
```

Here, we are performing bitwise **AND** between variables `a` and `b`.

#### 2. Bitwise OR Operator

The **bitwise OR** `|` operator returns **1** if at least one of the operands is **1**. Otherwise, it returns **0**.

The following truth table demonstrates the working of the **bitwise OR operator**. Let `a` and `b` be two operands that can only take binary values i.e. **1** or **0**.

| `a`  | `b`  |  `a | b`     |
|:----:|:------:|:------------:|
| 0    | 0      |  0           | 
| 0    | 1      |  1           |
| 1    | 0      |  1           |
| 1    | 1      |  1           |

Let us look at the bitwise **OR** operation of two integers **12** and **25**:

```cpp
12 = 00001100 (In Binary)
25 = 00011001 (In Binary)

Bitwise OR Operation of 12 and 25
    00001100
|   00011001
    _________
    00011101  = 29 (In decimal)

```


###### Example: Bitwise OR

```cpp
#include <iostream>

int main() {
    int a = 12, b = 25;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    cout << "a | b = " << (a | b) << endl;

    return 0;
}
```

###### Output
```sh
a = 12
b = 25
a | b = 29
```
The bitwise **OR** of `a = 12` and `b = 25` gives `29`.

#### Bitwise XOR Operator
The bitwise **XOR** `^` operator returns **1** if and only if one of the operands is **1**. However, if both the operands are **0**, or if both are **1**, then the result is **0**.

The following truth table demonstrates the working of the bitwise **XOR** operator. Let `a` and `b` be two operands that can only take binary values i.e. **1** or **0**.

| a  |  b |  a ^ b |
|:--:|:--:|:------:|
| 0  |  0 |    0   |
| 0  |  1 |    1   |
| 1  |  0 |    1   |
| 1  |  1 |    0   |

Let us look at the bitwise **XOR** operation of two integers `12` and `25`:

```cpp
12 = 00001100 (In Binary)
25 = 00011001 (In Binary)

Bitwise XOR Operation of 12 and 25
    00001100
^   00011001
    _________
    00010101  = 21 (In decimal)
```

###### Example: Bitwise XOR

```cpp
#include <iostream>

int main() {
    int a = 12, b = 25;

    cout << "a = " << a << endl;
    cout << "b = " << b << endl;
    cout << "a ^ b = " << (a ^ b) << endl;

    return 0;
}
```

###### Output
```sh
a = 12
b = 25
a ^ b = 21
```

The bitwise **XOR** of `a = 12` and `b = 25` gives `21`.

#### Bitwise Complement Operator

The bitwise **complement** operator is a **unary** operator (`works on only one operand`). It is denoted by `~` that changes binary digits **1** to **0** and **0** to **1**.

<p align="center">
  <img width="400" height="250" src="https://user-images.githubusercontent.com/83718460/208357889-859d3d1e-0b9a-4836-bdb3-46653a87e6d4.png">
  <p align="center">Bitwise Complement</p>
</p>

It is important to note that the **bitwise complement** of any integer **N** is equal to **-(N + 1)**. For example,

Consider an integer **35**. As per the rule, the bitwise complement of **35** should be **-(35 + 1) = -36**. Now, let's see if we get the correct answer or not.

```cpp
35 = 00100011 (In Binary)

// Using bitwise complement operator
~ 00100011 
 __________
  11011100
```
In the above example, we get that the **bitwise complement** of **00100011 (35)** is **11011100**. Here, if we convert the result into decimal we get **220**.

However, it is important to note that we cannot directly convert the result into decimal and get the desired output. This is because the binary result **11011100** is also equivalent to **-36**.

To understand this we first need to calculate the binary output of **-36**. We use **2's complement** to calculate the binary of negative integers.

##### 2's Complement

The **2's complement** of a number **N** gives **-N**.

In binary arithmetic, **1's complement** changes **0** to **1** and **1** to **0**.

And, if we add **1** to the result of the **1's complement**, we get the **2's complement** of the original number. 

For example,

```cpp

36 = 00100100 (In Binary)

1's Complement = 11011011 

2's Complement :   
11011011
 +     1
_________
11011100 

```

Here, we can see the **2's complement** of **36 (i.e. -36)** is **11011100**. This value is equivalent to the bitwise complement of **35** that we have calculated in the previous section.

Hence, we can say that the bitwise complement of **35 = -36**.

###### Example: Bitwise Complement

```cpp
#include <iostream>

int main() {
    int num1 = 35;
    int num2 = -150;
    cout << "~(" << num1 << ") = " << (~num1) << endl;
    cout << "~(" << num2 << ") = " << (~num2) << endl;

    return 0;
}
```

###### Output

```sh
~(35) = -36
~(-150) = 149
```

In the above example, we declared two integer variables `num1` and `num2`, and initialized them with the values of `35` and `-150` respectively.

We then computed their bitwise complement with the codes `(~num1)` and `(~num2)` respectively and displayed them on the screen.

The bitwise complement of `35 = - (35 + 1) = -36`
`i.e. ~35 = -36`

The bitwise complement of `-150 = - (-150 + 1) = - (-149) = 149`
`i.e. ~(-150) = 149`
This is exactly what we got in the output.

#### Shift Operators

There are two shift operators in C++ programming:

+ Right shift operator `>>`
+ Left shift operator `<<`

##### 1. Right Shift Operator

The right shift operator shifts all bits towards the right by a certain number of specified bits. It is denoted by `>>`.

When we shift any number to the right, the least significant bits are discarded, while the most significant bits are replaced by zeroes.

<p align="center">
  <img width="400" height="250" src="https://user-images.githubusercontent.com/83718460/208379050-5f1599db-6cae-48a6-a61b-455f8e94ea82.jpg">
  <p align="center">One bit Right Shift</p>
</p>

As we can see from the image above, we have a **4-bit** number. When we perform a **one-bit** right shift operation on it, each individual bit is shifted to the right by **1** bit.

As a result, the right-most bit is discarded, while the left-most bit remains vacant. This vacancy is replaced by a **0**.

##### 2. Left Shift Operator

The left shift operator shifts all bits towards the left by a certain number of specified bits. It is denoted by `<<`.

<p align="center">
  <img width="400" height="250" src="https://user-images.githubusercontent.com/83718460/208380582-0c8d5947-a3c7-4edd-8b4d-03d1018d6288.png">
  <p align="center">One bit Left Shift</p>
</p>

As we can see from the image above, we have a `4-bit` number. When we perform a `1 bit` left shift operation on it, each individual bit is shifted to the left by `1 bit`.

As a result, the left-most bit is discarded, while the right-most bit remains vacant. This vacancy is replaced by a `0`.

###### Example: Shift Operators

```cpp
#include <iostream>

int main() {

    // declaring two integer variables
    int num = 212, i;

    // Shift Right Operation
    cout << "Shift Right:" << endl;

    // Using for loop for shifting num right from 0 bit to 3 bits 
    for (i = 0; i < 4; i++) {
        cout << "212 >> " << i << " = " << (212 >> i) << endl;
    }

    // Shift Left Operation
    cout << "\nShift Left:" << endl;

    // Using for loop for shifting num left from 0 bit to 3 bits
    for (i = 0; i < 4; i++) {
        cout << "212 << " << i << " = " << (212 << i) << endl;
    }

    return 0;
}

```

###### Output

```sh
Shift Right:
212 >> 0 = 212
212 >> 1 = 106
212 >> 2 = 53
212 >> 3 = 26

Shift Left:
212 << 0 = 212
212 << 1 = 424
212 << 2 = 848
212 << 3 = 1696
```

From the output of the program above, we can infer that, for any number **N**, the results of the shift right operator are:

```cpp
N >> 0 = N
N >> 1 = (N >> 0) / 2
N >> 2 = (N >> 1) / 2
N >> 3 = (N >> 2) / 2
```

and so on.

Similarly, the results of the shift left operator are:

```cpp
N << 0 = N
N << 1 = (N << 0) * 2
N << 2 = (N << 1) * 2
N << 3 = (N << 2) * 2
```
and so on.

Hence we can conclude that,
```cpp
N >> m = [ N >> (m-1) ] / 2
N << m = [ N << (m-1) ] * 2
```

### Other Operators {#Other-Operators}

Here's a list of some other common operators available in C++. We will learn about them in later tutorials.

| Operator   |   Description                                              |                    Example                               |
|:--------:  |:-----------------------------------------------------------|:---------------------------------------------------------|
| `sizeof`   |  returns the size of data type                             |  `sizeof(int); // 4`                                     |
| `?:`       |  returns value based on the condition                      |  `string result = (5 > 0) ? "even" : "odd"; // "even" `  |
| `&`        |  represents memory address of the operand                  |  `&num; // address of num`                               |
| `.`        |  accesses members of struct variables or class objects     |  `s1.marks = 92; `                                       |
| `->`       |  used with pointers to access the class or struct variable |  `ptr->marks = 92;`                                      |    
| `<<`       |  prints the output value                                   |  `cout << 5;`                                            |
| `>>`       |  gets the input value                                      |  `cin >> num;`                                           |

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
    <a href="./c_basic_input_output.html" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="./e_flow_control.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---
