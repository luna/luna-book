Basic datatypes
===============

In this section will go through the basic datatypes available in Luna. You'll encounter some of these in every Luna program.

Numeric types
-------------

The basic numeric types in Luna are `Int`, representing integers of arbitrary size and `Real`, for floating point numbers.

> **[info] Changes ahead!**
>
> Currently, the type of a numeric literal is decided based on the presence of decimal point. This means, that `1` has the type `Int`, while `1.0` has the type `Real`. In the future releases of Luna, the numeric literals will be polymorphic, allowing to write expressions like `1.7 + 2`.

They support basic arithmetic operators and mathematical functions. Consult the relevant (TODO: LINK) part of standard library docs for more details.

Text
----

The basic type for text processing in Luna is, unsurprisingly, `Text`. Luna supports two kinds of text literals: interpreted and uninterpreted. The interpreted texts are wrapped in single quotes. They provide the capabilities to insert escaped character sequences such as `\n` etc. The uninterpreted strings are wrapped in double quotes and do not provide any such facilities. The only character that can be escaped in an uninterpreted text is `\"` itself.

> **[info] Changes ahead!**
>
> In the future releases of Luna the interpreted texts will also allow to insert arbitrary expressions, results of which will be then inserted into the resulting text. For example ``'Adding 2 and 2 gives `2 + 2` in result'`` will be evaluated to `'Adding 2 and 2 gives 4 in result'`.


Booleans
--------
Logical values are represented using the `Bool` class. It has two constructors: `True` and `False`. They support basic logical combinators such as `&&`, `||` or `not`. The most common function used for branching is `if_then_else`. It can be used in this form (i.e. `if_then_else condition valueWhenTrue valueWhenFalse`) or, more elegantly, in its _mixfix_ form:

```ruby
if condition then valueWhenTrue else valueWhenFalse
```

There is nothing special about this function, all the arguments are standard values and it returns a value just like any other function would:

```ruby
def reportRelationshipToSeven x:
    relation = if x > 7 then "greater than" else "less than or equal to"
    putStr (x.toText + " is " + relation + " seven")
```



Lists & Tuples
--------------

The most basic container types in Luna are tuples and lists.

Lists are arbitrary–length containers for same-type values. Some examples are `[3, 4, 5]` of type `List Int` or `['first', 'second', 'third']` of type ``List Text``. There are also some interesting functions and methods in the standard library, that return lists of desired shape. Some examples are:

```ruby
1.upto 5                       # => [1, 2, 3, 4, 5]
3.times "hello"                # => ["hello", "hello", "hello"]
[True, False] . cycle . take 5 # => [True, False, True, False, True]
```

Tuples are like lists, but they can store elements of different types and they have statically defined lengths. Some examples are:

```ruby
(1, "hello", False) :: (Int, Text, Bool)
("hi", 3.0)         :: (Text, Real)
```

> **[info] Changes ahead!**
>
> In the future versions of Luna, lists and tuples will be merged into one type – a list which fully understands its structure and allows to encode information about its length and different element types on type level. Thus you may expect code like ``["Hello", 32, False]`` to be valid Luna soon.


Optionals
---------

TODO Maybe & Either
