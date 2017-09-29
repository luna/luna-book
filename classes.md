# Classes & Objects

Objects are the basic blocks for bindling data and behaviors together. Luna's approach combines the approach known from Object Oriented languages with purely functional techniques, such as Algebraic Data Types.

## Introduction

Classes are defined in Luna with the `class` keyword. It is followed by definitions of constructors and methods. Let's consider this part of `Bool` class definition from the Luna standard library to better understand its different parts.

```
class Bool:
    True
    False
    
    def not: case self of
        True: False
        False: True
    
    def and that: case (self, that) of
        (True, True): True
        _: False
    
```

The first section in this code snippet defines constructors. Constructors are different variants of a given object. So the first part of the definition says "a Bool object is either True or False". Then we define some methods. Methods are just like functions, but they have one implicit argument – `self`. They are called using the `.` operator and the object before `.` becomes the `self` inside method definition.

Both methods defined in the above snippet use pattern matching – the `case` construction, that allows to change the behavior based on the constructor of some object.

We can use our newly defined `Bool` class as follows:

```True . negate . and False```

