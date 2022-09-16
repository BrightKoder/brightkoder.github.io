# Building Block of C Language

Like any other programming language, C also have few basic building blocks which are used to write the C programs.

Elements like Character set, Keywords or Reserved words, Operators and Variables etc called as the Building blocks of any programming language.

These foundational elements, Which we can use to create our application logic.


Here is the List of building blocks of C language.

1. Character set in C
2. Tokens
3. Identifiers & Rules to Defining Identifiers
4. Keywords
5. Comments
6. Constants
7. Variables
8. Operators
9. Datatypes
10. Statements

## Introduction of C Character Set

Majorly, there are two character sets in C language.

**Source Character Set:** This is the set of characters that can be used to write source code. Before preprocessing phase, the first step of C PreProcessor (CPP) is to convert the source code's encoding into Source Character Set (SCS). Eg: A, Tab, B, SPACE, \n, etc.

**Execution Character Set:** This is the set of characters that can be interpreted by the running program. After preprocessing phase, CPP converts character and string constant's encoding into Execution Character Set (ECS). Eg: A, B, \a, etc.

![chrset](https://user-images.githubusercontent.com/83718460/190428067-65cef8e3-f956-451b-9037-e0aaf215b74d.png)

By default, CPP uses UTF-8 encoding for both Source and Execution Character Sets. User can change them with below compiler flags.

  `-finput-charset` is used to set SCS.

  Usage: ``` sh gcc main.c -finput-charset=UTF-8```

  `-fexec-charset` is used to set ECS.

  Usage: ```sh gcc main.c -fexec-charset=UTF-8```


![Basic_chr_set](https://user-images.githubusercontent.com/83718460/190429649-815a8676-04b2-49c8-ac20-646b432484a7.PNG)

---
> Note: Basic Character Set is common between SCS and ECS

---

### Basic Character Set

Source and Execution Character sets have few common characters. The set of common characters is called Basic Character Set. Let's discuss more about it below:

#### Alphabets:
Which includes both uppercase and lowercase characters. ASCII code of uppercase characters is in the range [65, 90] whereas ASCII code of lowercase characters is in the range [97, 122]. Eg: A, B, a, b etc.
Uppercase and lowercase characters differ by just one bit.

**Utility Functions:** `isalpha`, `islower`, `isupper` check whether the character is alphabet, lowercase alphabet, uppercase alphabet respectively. `tolower`, `toupper` transforms the alphabets to appropriate case.

#### Digits:
Includes digits from 0 to 9 (inclusive). ASCII code of digits is in the range [48, 57]. Eg: 0, 1, 2 etc.

**Utility functions:** `isdigit` checks whether the input character is a digit. `isalnum` checks whether a character is alphanumeric character.

#### Punctuation/Special Characters:

 The default C locale classifies the below characters as punctuation characters.

**Utility functions:** `ispunct` checks whether a character is punctuation character. Below table contains the list of all punctuation characters, ASCII code and their usecases.

Character| ASCII   |Detail
:-------:|:-------:|:-------
!        | 33      | Exclamation mark, exclamation point, or bang.
"        | 34      | Quote, quotation mark, or inverted commas.
#        | 35      | Octothorpe, number, pound, sharp, or hash.
$        | 36      | Dollar sign or generic currency.
%        | 37      | Percent.
&        | 38      | Ampersand, epershand, or and symbol.
'        | 39      | Apostrophe or single quote.
(        | 40      | Open or left parenthesis.
)        | 41      | Close or right parenthesis.
*        | 42      | Asterisk, mathematical multiplication symbol, and sometimes referred to as a star.
+        | 43      | Plus.
,        | 44      | Comma.
-        | 45      | Hyphen, minus, or dash.
.        | 46      | Period, dot, or full stop.
/        | 47      | Forward slash, solidus, virgule, whack, and mathematical division symbol.
:        | 58      | Colon.
;        | 59      | Semicolon.
<        | 60      | Less than or angle brackets.
=        | 61      | Equal.
>        | 62      | Greater than or angle brackets.
?        | 63      | Question mark.
@        | 64      | Ampersat, arobase, asperand, at, or at symbol.
[        | 91      | Open bracket.
\        | 92      | Backslash or reverse solidus.
]        | 93      | Closed bracket.
^        | 94      | Caret or circumflex.
_        | 95      | Underscore.
'        | 96      | Acute, backquote, backtick, grave, grave accent, left quote, open quote, or a push.
{        | 123     | Open brace, squiggly brackets, or curly bracket.
}        | 125     | Close brace, squiggly brackets, or curly bracket.
~        | 126     | Tilde.


### Control Character Set

These characters range from ASCII code 0 to 31 (inclusive) and 127th character. They are visually absent, but they do affect the program in different ways. For example: \a (BEL) character may cause a beep sound or screen flashing when printed, \b (BS) character moves the cursor one step back (Unlike Backspace on the keyboard, which erases the previous character).

**Utility Functions:** `iscntrl` checks whether a character is a control character.

ASCII | Abbreviation                |
:----:|:----------------------------|
00    | NUL '\0' (null character)
01    | SOH (start of heading)
02    | STX (start of text)
03    | ETX (end of text)
04    | EOT (end of transmission)
05    | ENQ (enquiry)
06    | ACK (acknowledge)
07    | BEL '\a' (bell)
08    | BS '\b' (backspace)
14    | SO (shift out)
15    | SI (shift in)
16    | DLE (data link escape)
17    | DC1 (device control 1)
18    | DC2 (device control 2)
19    | DC3 (device control 3)
20    | DC4 (device control 4)
21    | NAK (negative ack.)
22    | SYN (synchronous idle)
23    | ETB (end of trans. blk)
24    | CAN (cancel)
25    | EM (end of medium)
26    | SUB (substitute)
27    | ESC (escape)
28    | FS (file separator)
29    | GS (group separator)
30    | RS (record separator)
31    | US (unit separator)
127   | DEL (delete)



### Escape Sequences: 
These characters are a part of the Execution Character Set. These characters need a backslash(\\) to identify them. It composes of 2 or more characters, but C PreProcessor treats them as a single character. Eg:\a, \b, \t etc...

### White-space characters: 
These characters are a part of the Source Character Set. They affect the text on display, but are visually blank.

**Utility Functions:** `isspace` checks whether a character is white-space character.


Character | ASCII | Detail
:--------:|:-----:|:----
<space>   | 32    | space (SPC)
\t        | 9     | horizontal tab (TAB)
\n        | 10    | newline (LF)
\v        | 11    | vertical tab (VT)
\f        | 12    | feed (FF)
\r        | 13    | carriage return (CR)


---
## Program

### Printing all characters

```c

#include <stdio.h>
#include <ctype.h>

int main() 
{
   printf("| Character | ASCII | Type        |\n");
   printf("| :-------: | ----: | :---------- |\n");
   for (int i = 32; i < 127; i++) {
       printf("|  %3c      | %3d   | ", i, i);
       if (isalpha(i))
           printf("Alphabet    |\n");
       else if (isdigit(i))
           printf("Digit       |\n");
       else if (ispunct(i))
           printf("Punctuation |\n");
       else if (isspace(i))
           printf("Space       |\n");
       else if (iscntrl(i))
           printf("Control     |\n");
   }
   return 0;
}

```

#### Output:

```c
| Character | ASCII | Type        |
| :-------: | ----: | :---------- |
|           |  32   | Space       |
|    !      |  33   | Punctuation |
|    "      |  34   | Punctuation |
|    #      |  35   | Punctuation |
|    $      |  36   | Punctuation |
|    %      |  37   | Punctuation |
|    &      |  38   | Punctuation |
|    '      |  39   | Punctuation |
|    (      |  40   | Punctuation |
|    )      |  41   | Punctuation |
|    *      |  42   | Punctuation |
|    +      |  43   | Punctuation |
|    ,      |  44   | Punctuation |
|    -      |  45   | Punctuation |
|    .      |  46   | Punctuation |
|    /      |  47   | Punctuation |
|    0      |  48   | Digit       |
|    1      |  49   | Digit       |
|    2      |  50   | Digit       |
|    3      |  51   | Digit       |
|    4      |  52   | Digit       |
|    5      |  53   | Digit       |
|    6      |  54   | Digit       |
|    7      |  55   | Digit       |
|    8      |  56   | Digit       |
|    9      |  57   | Digit       |
|    :      |  58   | Punctuation |
|    ;      |  59   | Punctuation |
|    <      |  60   | Punctuation |
|    =      |  61   | Punctuation |
|    >      |  62   | Punctuation |
|    ?      |  63   | Punctuation |
|    @      |  64   | Punctuation |
|    A      |  65   | Alphabet    |
|    B      |  66   | Alphabet    |
|    C      |  67   | Alphabet    |
|    D      |  68   | Alphabet    |
|    E      |  69   | Alphabet    |
|    F      |  70   | Alphabet    |
|    G      |  71   | Alphabet    |
|    H      |  72   | Alphabet    |
|    I      |  73   | Alphabet    |
|    J      |  74   | Alphabet    |
|    K      |  75   | Alphabet    |
|    L      |  76   | Alphabet    |
|    M      |  77   | Alphabet    |
|    N      |  78   | Alphabet    |
|    O      |  79   | Alphabet    |
|    P      |  80   | Alphabet    |
|    Q      |  81   | Alphabet    |
|    R      |  82   | Alphabet    |
|    S      |  83   | Alphabet    |
|    T      |  84   | Alphabet    |
|    U      |  85   | Alphabet    |
|    V      |  86   | Alphabet    |
|    W      |  87   | Alphabet    |
|    X      |  88   | Alphabet    |
|    Y      |  89   | Alphabet    |
|    Z      |  90   | Alphabet    |
|    [      |  91   | Punctuation |
|    \      |  92   | Punctuation |
|    ]      |  93   | Punctuation |
|    ^      |  94   | Punctuation |
|    _      |  95   | Punctuation |
|    `      |  96   | Punctuation |
|    a      |  97   | Alphabet    |
|    b      |  98   | Alphabet    |
|    c      |  99   | Alphabet    |
|    d      | 100   | Alphabet    |
|    e      | 101   | Alphabet    |
|    f      | 102   | Alphabet    |
|    g      | 103   | Alphabet    |
|    h      | 104   | Alphabet    |
|    i      | 105   | Alphabet    |
|    j      | 106   | Alphabet    |
|    k      | 107   | Alphabet    |
|    l      | 108   | Alphabet    |
|    m      | 109   | Alphabet    |
|    n      | 110   | Alphabet    |
|    o      | 111   | Alphabet    |
|    p      | 112   | Alphabet    |
|    q      | 113   | Alphabet    |
|    r      | 114   | Alphabet    |
|    s      | 115   | Alphabet    |
|    t      | 116   | Alphabet    |
|    u      | 117   | Alphabet    |
|    v      | 118   | Alphabet    |
|    w      | 119   | Alphabet    |
|    x      | 120   | Alphabet    |
|    y      | 121   | Alphabet    |
|    z      | 122   | Alphabet    |
|    {      | 123   | Punctuation |
|    |      | 124   | Punctuation |
|    }      | 125   | Punctuation |
|    ~      | 126   | Punctuation |

```

* `ctype.h` contains utility functions `isalpha`, `isdigit`. So, we included it at the top.
* Since Control characters are visually absent, we're not printing them, i.e., we started the loop at ASCII code 32.
* With the help of utility functions we're finding the type of the character.

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
    <a href="./introduction.html" class="my-ft-link">Prev</a>
  </div>
  <div class="my-footer2">
    <a href="operators.html" class="my-ft-link">Next</a>
  </div>
</div>
  
---
