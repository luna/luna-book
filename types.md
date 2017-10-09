# Types

Luna is equipped with a powerful type system. The philosophy behind it is to provide as much safety and useful hints as possible without restricting your expressive powers. In this chapter we'll introduce the basic concepts of Luna type system and the plans for its future development.

## Classes and constructors

Each object created with a constructor automatically gets the type of the constructor's class. So for example:

```haskell
Just 5               :: Maybe Int
Left (Right "hello") :: Either (Either a Text) b
```

> **[info] Changes ahead!**
>
> In the future versions Luna will have a much deeper understanding of the structure of objects and will retain that information on type level. It will allow you to describe types using constructors, not only classes. That means all of the following will be valid: 
> `Just 5 :: Just 5`
> `Just 5 :: Just Int`
> `Just 5 :: Maybe Int`

## Function types

Since functions in Luna are first-class citizens, each of them also has a type. The type of functions taking an argument of type `A` and returning a value of type `B` is `A -> B`. Since functions in Luna are curried by default, a two argument function is just a function that takes and argument and returns another function. So a function taking `A` and `B` and returning `C` can be typed as `A -> (B -> C)`. We can also drop the trailing parentheses, thus leaving us with `A -> B -> C`. 

## Type parameters

You will often encounter types like `Maybe a` or `Either Text a`. The lowercase variables are type parameters – any other type can be substituted for them. So if you have an expression of type `Either Text a`, it can serve as `Either Text Int`, `Either Text (List Text)` or `Either Text (Maybe a)`. Note that this substitution happens once for all the occurrences of a variable, so `id :: a -> a` can become `id :: Int -> Int`, but not `id :: Double -> Int`.