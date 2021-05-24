# RS-Hacking Challenge 2 
## Prize Pool $500
3 winners, first 50% ($250), second 35% ($175), third 25% ($125)
### Want to win?

Ultimately, the task is to get code from the language we made up, [chal](/chal.md), to run.

> You may use any language that will compile via github actions. The due date will be 6/20 @ 11:59 PST. Submit by adding `SwipeX` to your private github repo and DM'ing Swipe the link to your repo (for association).

This task will be broken up into 3 main components, there may be other ways to achieve this, however the following methodology **will be required**.

Note: You **MAY NOT** utilize any external libraries, only the standard library from the language of your choice.

### Parser

This component will take the text, along with the language syntax definition, and form a medium that can be translated into an AST. You may parse directly into the AST if you wish.

### Abstract Syntax Tree

For those who are not familiar, [refer here](https://en.wikipedia.org/wiki/Abstract_syntax_tree). You will design and create your own AST from the medium you created in the first step. 

### Processor

The job of the processor is to execute the AST.

## Submission

Your program must take in the path to a `.chal` file as an argument, and execute the program with the output being printed to the console.

## Sample Code

In order to reduce confusion, we are providing 5 code samples. If your project can correctly run all of these, you can consider it complete.

### Recursion
```
#simple recursive counter

(var counter 0)
(var max 0)

#entry point
(
    (print "Enter a max number: ")
    ($max (readInNumber))
    (recursiveIncr max)
    (print (append "Counter is at: " $counter))
)

(fun recursiveIncr ($counter max)
    (
        (
            if (equal $counter max) 
            $counter
            (recursiveIncr (++ $counter) max)
        )
    )
)
```
### Math/Unary/Binary
```
(
  (-- 
    (++ 
        (<< 
            (>> 
                (| 
                    (& 
                        (+ 5 
                            (- 7 
                                (* 9 
                                    (/ 10 2)
                                )
                            )
                        )
                    2)
                5)
            3)
        2)
      )
   )
)
```

### String
```
(var str "rshacking")

#entry point
(
    (print (charAt $str 0)) #r
    (print (removeAt $str 0)) #shacking
    (print (append $str "test")) #shackingtest
    (print (length $str)) #12
    (print (indexOf $str "g") #7 
)
```
### Errors
```
(var print 0) #default function name
(var 0 0) #variable name cannot be a number

(
    (print 0.5) #no error here
    (print "this" "should" "fail") #too many arguments supplied
)

#second entry point
(
    (print "whoops")
)

(fun test(param)) #no body defined
(fun test(param) ()) #method with same name already exists
```

### Fizzbuzz
```
(var counter 0)
(var max 100)

#entry point
(
    (recursiveIncr $max)
)

(fun recursiveIncr (max)
   (
        (print (fizzbuzz counter))

        (
            if (equal $counter max) 
            $counter
            (recursiveIncr (++ $counter) max)
        )
    )
)

(fun fizzbuzz (value)
    (
        (if (equal (* 15 (/ 15 value)) value)
            "Fizzbuzz"
            (if (equal (* 5 (/ 5 value)) value)
                "Buzz"
                (if (equal (* 3 (/ 3 value)) value)
                    "Fizz"
                     value
                )
            )
        )
    )
)
```

### Whitespace
```
(  (--     (++         (<<             (>>                 (|                     (&                         (+ 5 
                                                                  (- 7                                 (* 9 
  (/ 10 2)                                )
                            )                        )                    2)
                5)          3)
        2)      )
)
             )
```
(Yes, this should compile and run)