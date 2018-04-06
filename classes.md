# Classes & Objects

Objects are the basic blocks for bundling data and behaviors together. Luna's approach combines the approach known from Object Oriented languages with purely functional techniques, such as Algebraic Data Types.

## Introduction

Luna's notion of a class differs from what is known in most languages. If you are familiar with objects from Java or Python, you're in for a surprise.

First of all, Luna objects, besides having multiple fields, can also come in multiple, distinguishable flavors. This is known in functional programming as Algebraic Data Types and basically means that an object can be built using one of many available constructors and each of the constructors defines a different structure.

Using this technique we can say that any `Shape` is either a `Circle` or a `Rectangle`. Given an object of type `Shape` you are always sure it's one of those but you need to use [pattern matching](constructors.md) to discover which one was it.

However, thanks to methods, you can call some behaviors regardless of the constructor used. This means, given a `Shape` value, you may always use its `area` method, even though you may not know what was the real constructor used.

Another important property of objects in Luna is immutability. You may be used to mutable objects and expressions like `counter.count += 1` in other languages. In Luna every object is immutable – once it's created in a given way, it will never change. If you write `foo = Circle 15.0`, `foo` will always remain a `Circle` with the same radius, no matter how it is used. Any method that may seem to mutate the object, actually returns its changed version. So if you have a list and call its `sort` method, the original list remains unsorted – the sorted list is returned from the method instead and you need to assign this value to another variable if you want to use the sorted version later on.

## Class definition

> **[info] Changes ahead!**
>
> Currently, there is no way to define classes and methods using the visual editor. All the mechanisms described in these sections are text-only, the support for visual workflow is coming soon.

Classes in Luna are defined with the `class` keyword. It is followed by definitions of constructors and methods. Let's consider this definition of the `Shape` class to better understand its different parts.

```haskell
class Shape:
    Circle:
        radius :: Real
    Rectangle:
        width  :: Real
        height :: Real
    
    def perimeter: case self of
        Circle r: 2.0 * pi * r
        Rectangle w h: 2.0 * w + 2.0 * h
    
    def area: case self of
        Circle r: pi * r * r
        Rectangle w h: w * h
    
```

The first section in this code snippet defines constructors. Constructors are different variants of a given object. So the first part of the definition says "a Shape is either a Circle or a Rectangle". Then we define some methods. Methods are just like functions, but they have one implicit argument – `self`. They are called using the `.` operator and the object before `.` becomes the `self` inside method definition.

Both methods defined in the above snippet use pattern matching – the `case` construction, that allows to change the behavior based on the constructor of some object.

We can use our newly defined `Circle` class as follows:

```Circle 2.0 . area```

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
