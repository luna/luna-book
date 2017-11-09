# Functions

Functions are the basic units of reusable logic. A function is a piece of logic that takes any number of arguments, performs some operations and returns a result of these operations. Functions in Luna are also ordinary values, so you can pass them around freely. Most nodes you have used so far are actually functions. In this chapter you'll learn how to use functions and how to define them.

## Type of functions

Since functions are ordinary values, they need to have a type (all values in Luna are typed, remember?). The type of function taking an argument `A` and returning a `B` is `A -> B`. It's easy to remember when you think about the arrow as representing a transformation from type `A` to type `B`.

Multi–argument functions are typed using more arrows – for example a function taking a `Real`, an `Int` and returning a `Text` would be typed as `Real -> Int -> Text`. The last part of such an arrow chain is the return value, while all the parts before are consecutive arguments.