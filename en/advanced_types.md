## Methods

To achieve maximum levels of freedom and expressiveness, Luna allows calling methods on polymorphic arguments. Of course it's not always possible to infer what is the result type, so in this case we leave this unsolved until the real type is really needed. If you're familiar with the "duck typing" technique from dynamic languages, it's exactly the same in Luna, except when it's not really possible to call the function, you still get a compile-time error. Consider the following function:

```
def callSucc a: a.succ
```
What is its type? Since we haven't defined what is the type of `a`, we are assigning it a type parameter `b`. Now, what is the type of method `succ` on a type `b`? We can never know, as it depends on the implementation of a particular class that will be used. Hence, the type of `callSucc` is simply `b -> b.succ`. You can read it as "a function that takes an argument of type `b` and returns whatever the method `succ` of class `b` returns". We can now write `callSucc 1`, since the `succ` method is defined for `Int`s, but `callSucc "hello"` will result in a compile error.

## Type assumptions and the process of typechecking

Luna's typechecker stores some additional assumptions about type parameters, that need to be met by the types substituted for the variables. Those usually arise from manually typed functions and using methods on polymorphic values. Let's start with a simple example. The `+` operator is defined in Luna standard library as:

```python
def + :: a -> a -> a
def + x y = x.+ y
```
This definition allows us to write expressions like `5 + 7` or `"foo" + "bar"`, but will reject `"foo" + 5` (because arguments' types are different) or `Just 5 + Just 7` (because the `+` method is not defined for the `Maybe` class). So what is really going on here?

First of all, the user-specified type indicates that both the arguments and the return type need to be of the same type.
Second, the use of the method `+` indicates that the type `a` needs to have this method defined. Moreover, this method needs to take a single argument of type `a` and return a result also of type `a`.
All this allows us to describe the type of function `+` as:
```
+ :: a -> a -> a
```
for any `a` such that
```a.+ = a -> a```

All this is handled by the Luna compiler under the hood, so that you don't need to think about all the assumptions present.

Let's consider another example:

```def foo x: x.succ + 1```

What is the type of this function?
First of all, we can see that the result of `x.succ` is added to an `Int`, so (from the definition of `+` above) we know that `x.succ :: Int` and that the result of this function is also an `Int`. So the final type with the underlying assumptions is:

```
foo :: a -> Int
```
for any `a` such that
```a.succ = Int```

All those assumptions can grow with more complex, multiline functions. That's why Luna tracks them under the hood, revealing them only when some of them can't be satisfied.