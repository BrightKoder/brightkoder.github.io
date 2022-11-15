## Introduction 

C++ is a programming language created by Bjarne Stroustrup and his team at Bell Laboratories in 1979. C++ is a general-purpose programming language that was developed as an enhancement of the C language to include object-oriented paradigm.

C++ is designed to be a compiled language, meaning that it is generally translated into machine language that can be understood directly by the system, making the generated program highly efficient. For that, a set of tools are needed, known as the development toolchain, whose core are a compiler and its linker.

![image](https://user-images.githubusercontent.com/83718460/200758762-72a52e39-fc37-49d0-8170-3cab0ce4d4ec.png)

C++ is a middle-level language. It can be used to develop operating systems, browsers, games, and so on. C++ supports different ways of programming like procedural, object-oriented, functional, and so on. This makes C++ powerful as well as flexible. The basic syntax and code structure of both C and C++ are the same. 

## Features of C++

+ **Simple:** It is a simple language in the sense that programs can be broken down into logical units and parts, has a rich library support and a variety of data-types.

+ **Machine Independent but Platform Dependent:** A C++ executable is not platform-independent (compiled programs on Linux won’t run on Windows), however they are machine independent.

+ **Mid-level language:** It is a mid-level language as we can do both systems-programming (drivers, kernels, networking etc.) and build large-scale user applications (Media Players, Photoshop, Game Engines etc.)

+ **Rich library support:** Has a rich library support (Both standard ~ built-in data structures, algorithms etc.) as well 3rd party libraries (e.g. Boost libraries) for fast and rapid development.

+ **Speed of execution:** C++ programs excel in execution speed. Since, it is a compiled language, and also hugely procedural. Newer languages have extra in-built default features such as garbage-collection, dynamic typing etc. which slow the execution of the program overall. Since there is no additional processing overhead like this in C++, it is blazing fast.

+ **Pointer and direct Memory-Access:** C++ provides pointer support which aids users to directly manipulate storage address. This helps in doing low-level programming (where one might need to have explicit control on the storage of variables).

+ **Object-Oriented:** One of the strongest points of the language which sets it apart from C. Object-Oriented support helps C++ to make maintainable and extensible programs. i.e. Large-scale applications can be built. Procedural code becomes difficult to maintain as code-size grows.

+ **Compiled Language:** C++ is a compiled language, contributing to its speed.

## Applications of C++: 

+ Operating Systems & Systems Programming. e.g. Linux-based OS (Ubuntu etc.)
+ Browsers (Chrome & Firefox)
+ Graphics & Game engines (Photoshop, Blender, Unreal-Engine)
+ Database Engines (MySQL, MongoDB, Redis etc.)
+ Cloud/Distributed Systems

## Basics of C++

#### Program Structure

C++, like most programming languages, runs line by line, from top to bottom. Here is the structure of a C++.

![image](https://user-images.githubusercontent.com/83718460/200778222-9166129d-3b11-4a63-a7e4-bc2fe1bfdc4f.png)

#### First C++ Program – "Hello World!"

The “Hello World” program is the first step towards learning any programming language and is also one of the simplest programs you will learn. All you have to do is display the message “Hello World” on the screen. Let us now look at the program: 


###### Program
```cpp
// C++ program to display "Hello World"

// Header file for input output functions
#include <iostream>
using namespace std;

// Main() function: where the execution of program begins
int main()
{
	// prints hello world
	cout << "Hello World";

	return 0;
}

```
###### Output
```sh
Hello World!
```

Let us now understand every line and the terminologies of the above program: 

1. **// C++ program to display “Hello World”:** This line is a comment line. A comment is used to display additional information about the program. A comment does not contain any programming logic. When a comment is encountered by a compiler, the compiler simply skips that line of code. Any line beginning with `//` without quotes OR in between `/*…*/` in C++ is comment. 

2. **#include:** In C++,  all lines that start with `pound (#)` sign are called directives and are processed by a preprocessor which is a program invoked by the compiler. The #include directive tells the compiler to include a file and `#include<iostream>`. It tells the compiler to include the standard iostream file which contains declarations of all the standard input/output library functions.

3. **using namespace std:** This is used to import the entirety of the std namespace into the current namespace of the program. The statement using namespace std is generally considered a bad practice. When we import a namespace we are essentially pulling all type definitions into the current scope. The std namespace is huge. The alternative to this statement is to specify the namespace to which the identifier belongs using the `scope operator(::) `each time we declare a type.

4. **int main():** This line is used to declare a function named `main` which returns data of integer type. A function is a group of statements that are designed to perform a specific task. Execution of every C++ program begins with the `main()`function, no matter where the function is located in the program. So, every C++ program must have a `main()` function.

5. **{ and }:** The opening braces `{` indicates the beginning of the main function and the closing braces `}` indicates the ending of the main function. Everything between these two comprises the body of the main function.

6. **std::cout<<“Hello World!”;:**  This line tells the compiler to display the message `Hello World!` on the screen. This line is called a statement in C++. Every statement is meant to perform some task. A semi-colon `;` is used to end a statement. Semi-colon character at the end of the statement is used to indicate that the statement is ending there. The `std::cout` is used to identify the standard character output device which is usually the desktop screen. Everything followed by the character `<<` is displayed to the output device.

7. **return 0;:** This is also a statement. This statement is used to return a value from a function and indicates the finishing of a function. This statement is basically used in functions to return the results of the operations performed by a function.

#### Character Sets in C++
The input and output of a program are made up of characters and symbols. C++ Character Set is a collection of characters and symbols that have a specified meaning. It consists of:

+ **Letters:** uppercase (A-Z) and lowercase (a-z) alphabets.
+ **Digits:** Numbers from 0-9.
+ **Special characters:** There are various special characters like , ; \ _ ? : etc.
+ **White spaces:** blank space, new line, horizontal tab and carriage return.

### Tokens in C++

A token is the smallest unit of a program that the compiler understands. In C++, Tokens are divided into

+ Keywords
+ Identifiers
+ Constants
+ Strings
+ Special Symbols
+ Operators

![image](https://user-images.githubusercontent.com/83718460/200841049-26067581-9902-4525-b406-7e8204bf98e9.png)

#### C++ Keywords

**Keywords** are predefined words that have special meanings to the compiler. 

For example,
```cpp
int money;
```
Here, `int` is a keyword that indicates `money` is a variable of type **integer**.

Here is a list of all C++ keywords. `(as of C++17)`

|           |              |                   |              |
|-----------|--------------|-------------------|--------------|
| alignas   | decltype	   | namespace	       | struct       |
| alignof   | default	   | new	           | switch       |
| and	    | delete	   | noexcept	       | template     |
| and_eq    | do	       | not	           | this         |
| asm	    | double	   | not_eq	           | thread_local |
| auto	    | dynamic_cast | nullptr	       | throw        |
| bitand    | else	       | operator	       | true         |
| bitor	    | enum	       | or	               | try          |
| bool	    | explicit	   | or_eq	           | typedef      |
| break	    | export	   | private	       | typeid       |
| case	    | extern	   | protected	       | typename     |
| catch	    | false	       | public	           | union        |
| char	    | float	       | register	       | unsigned     |
| char16_t  | for	       | reinterpret_cast  | using        |
| char32_t  | friend	   | return	           | virtual      |
| class	    | goto	       | short	           | void         |
| compl	    | if	       | signed	           | volatile     |
| const	    | inline	   | sizeof	           | wchar_t      |
| constexpr | int	       | static	           | while        |
| const_cast| long	       | static_assert	   | xor          | 
| continue  | mutable	   | static_cast       | xor_eq       |

---
> **Note:** As C++ is a case sensitive language, all keywords must be written in lowercase.

---

#### C++ Identifiers

Identifiers are the unique names given to variables, classes, functions, or other entities by the programmer. For example,

```cpp
int money;
double accountBalance;
```
Here, `money` and `accountBalance` are identifiers.

##### Rules for naming identifiers
+ Identifiers can be composed of letters, digits, and the underscore character.
+ It has no limit on name length.
+ It must begin with either a letter or an underscore.
+ It is case-sensitive.
+ We cannot use keywords as identifiers.
+ We can choose any name as an identifier if we follow the above rules. However, we should give meaningful names to the identifier that makes sense.

##### Examples of good and bad identifiers

| Invalid Identifier | Bad Identifier |	Good Identifier |
|--------------------|----------------|-----------------|
| Total points	     | T_points	      | totalPoint      |
| 1list	             | list_1         |	list1           |
| float	             | n_float	      | floatNumber     |

#### Constant

A constant, like a variable, is a memory location where a value can be stored. variables, constants never change in value. You must initialize a constant it is created.

Constant is declared with a const keyword whose value never changes in the execution of the program. The Fixed value is known as literals.

![Constants-in-C](https://user-images.githubusercontent.com/83718460/201593671-edac7ed7-c227-4316-8d96-a963b539c317.jpg)

A constant is a token in C++ that corresponds to a number, character, or character string that can be used as a value in a program. Every constant has a type and a value on the basis of which, constants are categorised into the following types:

+ **Floating Point Constants:** It is a decimal number that represents a signed real number. The representation of a signed real number includes an integer portion, a fractional portion, and an exponent. 
```cpp
e.g.
const float f = 23.5f;

const double d = 34.6;
```
+ **Integer Constants:** It is a decimal (base 10), octal (base 8), or hexadecimal (base 16) number that represents an integral value. We use these to represent integer values that cannot be changed.
```cpp
e.g.
const int a = 10;

```

+ **Character Constants:** A "character constant" is formed by enclosing a single character from the representable character set within single quotation marks (' '). 
```cpp
e.g.
const char ch = 'A';

```

+ **String Constants:** A "String constant" is formed by enclosing a multiple character together from the representable character set within double quotation marks (" "). 
```cpp
e.g.
const string str = "ABC";

```

+ **Enumeration Constants:** The named integer identifiers that are defined by enumeration types are called enumeration constants.
```cpp
#include <iostream>
int main()
{
   enum Days { Sunday, Monday, Tuesday,
            Wednesday, Thursday, Friday, Saturday };

   Days today;
   today = Monday;

   if (today == Sunday || today == Saturday)
      std::cout << "\nGotta' love the weekends!\n";
   else
      std::cout << "\nBack to work.\n";

   return 0;
}
```

#### Strings

Just like characters, strings in C++ are used to store letters and digits. Strings can be referred to as an array of characters as well as an individual data type.

It is enclosed within double quotes, unlike characters which are stored within single quotes. The termination of a string in C++ is represented by the null character, that is, `\0`. The size of a string is the number of individual characters it has.

In C++, a string can be declared in the following ways:

```cpp
char name[30] = "Hello World!"; // The compiler reserves 30 bytes of memory for the string.

char name[] = "Hello World!"; // The compiler reserves the required amount of memory for the string.

char name[30] = { 'H' , 'e' , 'l' , 'l' , 'o', 'W', 'o', 'r','l','d','!'}; // This is how a string is represented as a set of characters.

string name = "Hello World"; // The compiler reserves 32 bytes of memory.
```

#### Special Symbols

Apart from letters and digits, there are some special characters in C++ which help you manipulate or perform data operations. Each special symbol has a specific meaning to the C++ compiler.

Here is a table which illustrates some of the special characters in C:

|Special Character  |	Trivial Name                | Function                                                                                                          |
|-------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------------|
|    `[ ]`	        |  Square brackets              | Used for single dimensional and multidimensional subscripts of arrays.                                            |     
|    `( )`	        |  Simple brackets	            | Used for function calls and parameters.                                                                           |
|    `{ }`	        |  Curly braces	                | Used to indicate the beginning and end of a code block.                                                           |
|     `,`	        |  Comma                        | Used to separate multiple statements like parameters in a function.                                               |
|     `:`           |  Colon                        | Used to invoke an initialization list.                                                                            |
|     `;`           |  Semicolon                    | used to mark the end of statements.                                                                               |
|     `#`	        |  Hash / Pound / Preprocessor  | The hash symbol represents a preprocessor directive used for denoting the use of a header file                    |
|     `*`           |  Asterisk	                    | We use the asterisk symbol in various respects such as to declare pointers, used as an operand for multiplication |
|     `~`           |  Tilde	                    | We use the tilde symbol as a destructor to free memory                                                            |
|     `.`	        |  Period / dot                 | The use the dot operator to access a member of a structure 

#### Operators

Operators are symbols that operate on operands. These operands can be variables or values. Operators help us to perform mathematical and logical computations.

We will see in-depth operators in next tutorial.                                           

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
    <a href="https://brightkoder.github.io/" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="./data_types.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---
