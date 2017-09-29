Basic datatypes
===============

In this section will go through the basic datatypes available in Luna. You'll encounter some of these in every Luna program.

Numeric types
-------------

The basic numeric types in Luna are `Int`, representing integers of arbitrary size and `Real`, for floating point numbers.

> **[info] Changes ahead!**
> Currently, the type of a numeric literal is decided based on the presence of decimal point. This means, that `1` has the type `Int`, while `1.0` has the type `Real`. In the future releases of Luna, the numeric literals will be polymorphic, allowing to write expressions like `1.7 + 2`.

They support basic arithmetic operators and mathematical functions. Consult the relevant (TODO: LINK) part of Std docs.

Text
----

The basic type for text processing in Luna is, unsurprisingly, `Text`. Luna also supports two kinds of text literals. TODO DESCRIBE.

Booleans
--------

TODO

1. `if_then`
2. `if_then_else`

Lists & Tuples
--------------

The most basic compound types in Luna are tuples and lists.

Lists are arbitrary–length containers for same-type values. Some examples are `[3, 4, 5]` of type `[Int]` or `['first', 'second', 'third']` of type ``[Text]``. There are also some interesting functions and methods in the standard library, that return lists of desired shape. Some examples are:

    1.upto 5                       # => [1, 2, 3, 4, 5]
    3.times "hello"                # => ["hello", "hello", "hello"]
    [True, False] . cycle . take 5 # => [True, False, True, False, True]

Tuples are like lists, but they can store elements of different types and they have a statically defined lengths. Some examples of tuples are:

    (1, "hello", False) :: (Int, Text, Bool)
    ("hi", 3.0)         :: (Text, Real)

> **[info] Changes ahead!**
> In the future versions of Luna, lists and tuples will be merged into one type – a list which fully understands its structure and allows to encode information about its length and different element types on type level. Thus you may expect code like ``["Hello", 32, False]`` to be valid Luna soon.


Optionals
---------

TODO Maybe & Either
