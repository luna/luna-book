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

## Constructors

Most classes in Luna have at least one constructor. They are used to create instances of the class and to pattern match on the objects. The basic way to define them is as follows:

```haskell
class Shape:
    Circle:
        center :: Point
        radius :: Real
    Rectangle:
        topLeft     :: Point
        bottomRight :: Point
```

This snippet defines a `Shape` class with two constructors: `Circle` and `Rectangle`. Each of the constructors stores information essential for a given kind of shape.

You may also omit the field names, resulting in code like this:

```haskell
class Shape:
    Circle    Point Real
    Rectangle Point Point
```

While this code is much more concise, it has some drawbacks. First of all it isn't clear from the definition what the fields are really representing. Moreover, you lose the ability to access the fields by name.

> **[info] Changes ahead!**
>
> Currently Luna allows accessing fields by name only when there is exactly one constructor present. This behavior will be extended in the near future, providing great capabilities for multi-constructor classes.


Finally, when there is only one constructor present, you may skip its name. In this case Luna will create a constructor with the same name as the class name:

```haskell
class Vector:
    x y z :: Real
```

This snippet defines a `Vector` class and a `Vector` constructor with three `Real` fields: `x`, `y` and `z`.

