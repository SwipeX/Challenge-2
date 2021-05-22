# chal-lang

## Syntax

Syntax is prefix notation, mostly modeled after LISP. Parenthesis surround each operation, in which all elements are separated by whitespace. 

(_operator_ _operands..._) 
>Ex: (4 >> 10) - 4 + 5 would be written as: (+ 5 (- 4 (>> 4 10)))

## Operators

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
    shiftLeft <<
    shiftRight >>
    and &
    or |
#### Equality
    equal ==
    notEqual !=
    greaterThan >
    lessThan <
#### String
    charAt
    removeAt
    append
    length
    indexOf
#### Functions
    (if expression true false) -> evaluates @expression, and continues execution on true branch or false branch
    (readInString) -> returns a string read from the console
    (readInNumber) -> returns a number rad from the console
    (print operand) -> prints a @operand to the console
    (exit operand) -> exits the process with code @operand
### User Defined Functions
>(Modulus 40 5) will call a defined function `Modulus` with the operands that follow (or error).
##### Defining
The syntax for defining functions is:

_(fun name (operands...) (function body))_, IE `(fun incr(number amount) (+ number amount))`

As always, whitespace is ignored so the body can be on a new line(s).
##### Referencing
The syntax for referencing a function is:

`(incr 10 5)`, which using the function above, would return 15.
### Variables
Variables are global and may be declared either before code execution or after. 

##### Defining
The syntax for defining variables is:

_(var name value)_, IE `(var counter 0)`
##### Referencing
The syntax for referencing a variable as an operand is `$name`, IE `(Add 5 $counter)`
##### Setting values
The syntax for setting a variable's value is `($name value)`, IE `($counter (divide 10 2))` would set counter to 5. Keep in mind this statement would return this value as well.
### Comments
Comments can appear anywhere in code, but end processing until the next newline. Comments are denoted by a leading '#'

```#This is a comment```
### Error Handling
Errors will be handled by printing to the console and halting program execution immediately.

The following code ```(multiply "hello" "world")``` in the most basic sense would print
>Unexpected parameter type in function `multiply`, expected numeric value.


## Code Example
```
#Simple recursive counter

(var counter 0)
(var max 0)

(
    (print "Enter a max number: ")
    ($max readInNumber)
    (recursiveIncr counter max)
    (print (append "Counter is at: " counter))
)

(fun recursiveIncr (counter max)
    (
        if (equal counter max) 
        counter
        (recursiveIncr (++ counter) max)
    )
)
```
