# Notes-Scala

## Call-by-value, Call-by-name and termination:

__Question__ : find an expression that terminates under CBN but not under CBV.

> `def first(x: Int, y: Int) = x`


__Answer__ :

> `first(1, loop)`

Under CBN,  it simply terminates as loop is not used. However, CBV has to reduce/unpack loop even though the function doesn't use it.

**Scala still uses call by value by default, as it has a much predictable behaviour. However, the option for call-by-name still exists, shown when the type of a function parameter starts with =>**

__Example:__
> `def constOne(x: Int, y: => Int) = 1`
----------------------------
## Conditionals and Value Definitions:

To express choosing between alternatives, Scala has a conditional expression if-then-else.

It resembles an if-else in Java, but is used for expressions, not statements.

__Example__ :
>`def abs(x: Int) = if x >= 0 then x else -x`

---------------

## Blocks and Lexical scope:

It's good functional programming style to split up a task into many small functions However, the sub-functions that are only relevant to a certain function that is user facing should be hidden. 

Achieving this and at the same time avoiding "name-space pollution" is done by putting the auxiliary functions inside our main function

-------------

## Tail Recursion:
In short, Recursive functions that only use one stack frame.

The cool part: we can force the compiler to optimize for tail recursion in during compile time, using the 
`@tailrec` annotion.

If a function is annotated, then it's implementation isn't tail recursive and an error would be issued. 

-------------------------------

## Higher-Order Functions:

> def sum (F: Int => Int, a Int, b Int): Int =

where F is an aux function passed to the more general pattern of sum.

this couple with **Anonymous functions** makes it so function can be written even shorter as in:

def sumCubes(a: Int, b: Int) = sum(x => x * x * x, a , b)

----------------------------

## Currying :

> def sum(f: Int => Int): (Int, Int) => Int 

sum is now a function that returns another function that returns an int.
