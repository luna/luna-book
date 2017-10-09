# Types

Luna is equipped with a powerful type system. The philosophy behind it is to provide as much safety and useful hints, without restricting your expressive powers. In this chapter we'll introduce the basic concepts of Luna type system and the plans for its future development.

## Classes and constructors

Each object created with a constructor automatically gets the type of the constructor's class. So for example:

```haskell
Just 5               :: Maybe Int
Left (Right "hello") :: Either (Either a Text) b
```

> **[info] Changes ahead!**
>
> In the future versions Luna will have a much deeper understanding of the structure of objects and will retain that information on type level. That means all of the following will be valid: 
> `Just 5 :: Just 5`
> `Just 5 :: Just Int`
> `Just 5 :: Maybe Int`