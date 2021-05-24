# chal-lang

## Syntax

Syntax is prefix notation, mostly modeled after LISP. Parenthesis surround each operation, in which all elements are separated by whitespace. 

(_operator_ _operands..._) 
>Ex: (4 >> 10) - 4 + 5 would be written as: (+ 5 (- 4 (>> 4 10)))
---

## Types

All types are implied, and for the sake of simplicity, may not change during runtime. This means that a variable declared as `true` may not later be set to `5`.

The types that exist are:

- Number (32 bit IEEE float as backing type) [refer here](https://en.wikipedia.org/wiki/Single-precision_floating-point_format)
- Boolean (true/false)
- String (max length 255)
---

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
    shiftLeft << (base operand)
    shiftRight >> (base operand)
    and & (base operand)
    or | (base operand)
#### Equality
    equal ==
    notEqual !=
    greaterThan >
    lessThan <
#### String
    charAt (string index)
    removeAt (string index)
    append (string stringToAppend)
    length (string)
    indexOf (stringtoSearch stringToFind)
#### Functions
    (random min max) -> returns a random whole number between min and max
    (if expression true false) -> evaluates @expression, and continues execution on true branch or false branch
    (readInString) -> returns a string read from the console
    (readInNumber) -> returns a number rad from the console
    (print operand) -> prints a @operand to the console
    (exit operand) -> exits the process with code @operand

---
## Defined Functions
>(Modulus 40 5) will call a defined function `Modulus` with the operands that follow (or error).

### Defining
The syntax for defining functions is:

`(fun name (operands...) (function body))`, IE `(fun incr(number amount) (+ number amount))`

As always, whitespace is ignored so the body can be on a new line(s).

Function names must start with an alpha character. `(fun 234 () ())` should throw a parse error.

### Referencing

The syntax for referencing a function is:

`(incr 10 5)`, which using the function above, would return 15.

---

## Variables
Variables are global and may be declared anywhere that is not a code block.

Variable names must start with an alpha character. `(var 234 0)` should throw a parse error.

### Defining
The syntax for defining variables is:

_(var name value)_, IE `(var counter 0)`


### Referencing
The syntax for referencing a variable as an operand is `$name`, IE `(add 5 $counter)`


### Setting
The syntax for setting a variable's value is `($name value)`, IE `($counter (divide 10 2))` would set counter to 5. Keep in mind this statement would return this value as well.

---

## Comments
Comments can appear anywhere in code, and halt code processing until the next line. Comments are denoted by a leading '#'.

```#This is a comment```

---

## Error Handling
Errors will be handled by printing to the console and halting program execution immediately.

The following code ```(multiply "hello" "world")``` in the most basic sense would print
>Unexpected parameter type in function `multiply`, expected numeric value.

Functions/Operators that expect a certain type should also error. For example:
    
    #declare var test as 77
    (var test 77)
    #set test to the negation of test
    ($test !$test)

Should produce an error, as the negate operator expects only boolean values. 

---

## Entry point
Similar to kotlin or javascript, code entry will start and finish at the first set of blank parenthesis. Refer to the below example for more context.

This can occur anywhere in a file, and should produce an error if multiple entry points are found.

---

## Code Example
```
#simple recursive counter

(var counter 0)
(var max 0)

#entry point
(
    (print "Enter a max number: ")
    ($max (readInNumber))
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
