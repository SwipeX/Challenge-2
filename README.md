# chal-lang

## Syntax

Parenthesis surround each operation, in which all elements are separated by whitespace.

(_operator_ _operands..._)
>Ex: (+ 5 (- 4 (>> 4 10)))

**Note: Execution should start from the first parenthesis that is not part of a variable declaration.**


### Overview

>A simple language with a LISP style prefix syntax. Basic math, unary, and binary operators are supported, along with function calls and global variables. camelCase is the preferred convention.


#### Math
    add +
    subtract -
    multiply *
    divide / 
    exponent ^
#### Unary
    increment ++
    decrement --
    negate !
#### Binary
    shiftL <<
    shiftR >>
    and &
    or |
#### String
    charAt
    removeAt
    append
    length
    indexOf
#### Functions
    (Print operand) -> prints a @operand to the console
    (Exit operand) -> exits the process with code @operand
#### User Defined Functions
>(Modulus 40 5) will call a defined function `Modulus` with the operands that follow (or error).
#### Variables
Variables are global and may be declared either before code execution or after.

*Variables can contain code that may execute, as well as other variables.*
##### Defining
The syntax for defining variables is:

_GLOBAL_ _name_(_value_), IE `GLOBAL counter(+ 55 7)`
##### Referencing
The syntax for referencing a variable as an operand is `$name`, IE `(Add 5 $counter)`
##### Setting
The syntax for referencing a variable as an operand is `($name operand)`, IE `($counter (divide 10 2))` would set counter to 5.
#### Comments
Comments can appear anywhere in code, but end processing until the next newline. Comments are denoted by a leading '#'
```#This is a comment```
#### Error Handling
Errors will be handled by printing to the console and halting program execution immediately.

The following code ```(multiply "hello" "world")``` in the most basic sense would print
>Unexpected parameter type in function `Add`, expected numeric value and got string.
