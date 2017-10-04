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

This snippet defines a `Vector` class and a `Vector` constructor with three `Real` fields: `x`, `y` and `z`. Luna also automatically defines field accessors, so you can now write code like this:

```
v1 = Vector 1.0 2.0 3.0
v2 = v1.y = 3.14
v1.x  # returns 1.0
v2.y  # returns 3.14
```

## Pattern Matching

Pattern matching is a mechanism allowing to discover which particular constructor was used to create a given object. It also allows to bring the values of fields (even unnamed) of the constructor into the scope. Let's get back to the `Shape` example once again. Suppose you have facilities for rendering circles and rectangles and you need to render `Shape`s. This can be accomplished with a simple pattern match:

```
def render shape:
    case shape of
        Circle c r:      renderCircle c r
        Rectangle tl br: renderRectangle tl br
```

## Parametric Polymorphism

Classes in Luna can also take type parameters, making them polymorphic in some values. For an example, consider the previous definition of `Vector`:

```haskell
class Vector:
    x y z :: Real
```

What if we wanted a `Vector` of `Int`s? In the current approach, it would require us to create another class just for this purpose. We can, however pass a type parameter to the `Vector` class:

```haskell
class Vector a:
    x y z :: a
```

With the current implementation, we can create vectors containing elements of any type, such as `Real`s, `Int`s, `Bool`s etc.

```haskell
Vector "hello" "world" "!" :: Vector Text
Vector 1 2 3               :: Vector Int
Vector 1.0 2.0 3.0         :: Vector Real
```

It is also possible to implement methods that assume some additional properties of the type `a` (such as supporting arithmetic operations, or having defined some other methods). For example:

```haskell
class Vector a:
    x y z :: a
    
    def dotProduct that:
        self.x * that.x + self.y * that.y + self.z * that.z
```

The `dotProduct` method will work with any elements supporting addition and multiplication, so using it with `Int`s or `Real`s is fine, while using it with `Text` results in a type error.

```
Vector 1 2 3 . dotProduct (Vector 4 5 6)                           # returns 32   :: Int
Vector 1.0 2.0 3.0 . dotProduct (Vector 4.0 5.0 6.0)               # returns 32.0 :: Real
Vector "hello" "world" "!" . dotProduct (Vector "foo" "bar" "baz") # does not compile
```
