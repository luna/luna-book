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

