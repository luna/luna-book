# Calling C Functions

Starting from the 1.3 beta version, Luna comes equipped with the ability to call foreign C functions from object files. This document describes how to use this system to create C based libraries.

## Object files

Object files contain compiled code that can be dynamically loaded and used by other programs. The most common types are `.so` files on Linux, `.dylib` files on macOS and `.dll` on Windows.
Luna is able to work with object files coming from two sources:
1. System-wide available dynamic libraries. If a library is installed on your machine, Luna will be able to use it. Unfortunately, this requires all the users of your library to have the dynamic library installed in their systems. For most libraries this is not a good solution, it will, however, work fine for bindings to the most popular libraries and for quick prototyping.
2. Object files inside the project tree. You can drop any shared object file into the `native_libs/PLATFORM` directory inside your project (`PLATFORM` is `macos`, `linux` or `windows`) and use it from Luna. This is a great solution for making sure users are able to use your library without any external dependencies. It's also the only way to include your own C extension or wrapper.

## Using a shared library

> **[info] Changes ahead!**
>
> This describes the bare-bones way of interacting with foreign objects. There are some syntactic changes coming soon to cut down on boilerplate. The basic concepts, however, will remain unchanged.


OK, so you have your shared library in place, how to actually use it from Luna? For this example, we'll assume that we're working with the following directory structure:

```
MyProject/
  MyProject.lunaproject
  src/
    Main.luna
  native_libs/
    macos/
      libawesome.dylib
    linux/
      libawesome.so
    windows/
      libawesome.dll
```
The object files in this example contain just a single function, with the following C signature:
```
int awesomeFunction(int);
```
How do we use it?

### Resolving the symbol

The workhorse of our FFI (Foreign Function Interface) is the `lookupSymbol` function from `Std.Foreign` module. It takes a shared object file name and a name of the symbol to lookup, and returns a `FunPtr` object. The library resolution takes into account the most common naming conventions, so that it is possible to use the same call with a file named `awesome.dylib` as well as `libawesome.4.so`.
So, in our example, you can just write:
```
def awesomeFunction i:
    funPtr = lookupSymbol "awesome" "awesomeFunction"
```

### Calling the FunPtr

Now that we've obtained the function pointer, it's time to call the function.
This is what the `call` method of `FunPtr` does. It takes two arguments – a representation for the output type and a list of objects of type `CArg`, representing the function arguments. Note that not every type can be represented as a C argument. The types that can (numeric types, pointers and a few more) are converted using their `toCArg` method.
So, back to our example. The `awesomeFunction` expects and `int` and returns an `int`. Note that Luna's `Int`s are different from C's, so the latter are represented by the class `CInt`. This is what our function call looks like:

```
def awesomeFunction i:
    funPtr = lookupSymbol "awesome" "awesomeFunction"
    result = funPtr . call CInt [i.toCArg]
```

### Translating between C and Luna data types

We have successfully called a C function. It is not very usable for most Luna code though – it requires us to use the C types throughout the program. We'll fix that with a few conversion methods. First of all, the function argument needs to be a `CInt`. Most Luna programs, however, use standard `Int`s and these cannot easily be represented in C. This can be fixed with the help of `CInt.fromInt` function, which converts an ordinary `Int` object into a `CInt`. 
It also returns a `CInt`, which again is not very handy. This can be fixed with the help of `toInt` method of `CInt`. The final version of our wrapper, which operates on `Int`s and from the outside is nearly indistinguishable from pure Luna code looks like this:

```
def awesomeFunction i:
    iArg = CInt.fromInt i
    funPtr = lookupSymbol "awesome" "awesomeFunction"
    result = funPtr . call CInt [iArg.toCArg]
    result.toInt
```

## Basic C Types

Luna defines counterparts of the standard C types in the `Std.Foreign.C.Value` module. This section is a short overview of all of them.

### Integer types

There is a counterpart for integral types commonly used throughout C codebases. All these wrappers have a common API – they define the `fromInt` and `toInt` methods, support comparison and basic arithmetic operators. The following table shows the C types and their Luna counterparts.

C Type        | Luna Class
--------------|-----------
(signed) char | CChar
unsigned char | CUChar
wchar_t       | CWChar
(signed) int  | CInt
unsigned int  | CUInt
(signed) long | CLong
unsigned long | CULong
int8_t        | CInt8
uint8_t       | CUInt8
int16_t       | CInt16
uint16_t      | CUInt16
int32_t       | CInt32
uint32_t      | CUInt32
int64_t       | CInt64
uint64_t      | CUInt64
size_t        | CSize

### Floating point numbers

Luna defines the `CDouble` and `CFloat` classes as counterparts of C's `double` and `float`, respectively. Both classes define `fromReal` and `toReal` methods for conversion between them and Luna's `Real`. They also support basic arithmetic and comparison operators.

## Pointers

> **[info] Changes ahead!**
>
> Since version 1.4 Luna will support managed pointers – pointers with a finalizer to run when the pointer is garbage collected. Currently, you need to carefully plan out memory management, as there is no way to free a pointer automatically.


The basic pointer type is just `Pointer`. It takes a single argument denoting the type of its content. So, for example, `Pointer CInt` corresponds to `int*` in C, while `Pointer (Pointer None)` is `void**`.

### Creating and freeing pointers

To create a pointer able to hold a single value of type `X` use the `malloc` method on pointer class: 
```
ptr = Pointer X . malloc
```
For this to work, the `X` object must define a `byteSize` method, returning the size in bytes of the structure.
You can also use `mallocElems` to create arrays like so:
```
arr = Pointer CInt . mallocElems 40
```
Any pointer can be freed using its `free` method – if you're done with your `ptr` just call `ptr.free`.

### Reading and writing

Reading a pointer can be accomplished by its `read` method. It works on a `Ptr X` and returns a value of type `X`. Keep in mind that in order for this to work, the `X` type must define a `readPtr` method that takes a bare pointer and plucks the fields one by one.

Similarly, to write a value to `ptr` of type `Pointer X`, call `ptr.write x`. Again, this requires the type `X` to define `writePtr` method.

For the basic C types, the required methods are already defined in the standard library.

### Pointer arithmetic

Any pointer can be moved by a specified number of bytes using the `ptr.moveBytes i` method – it returns a new pointer, resulting from adding `i` bytes to `ptr`.
There is also a `moveElems` method, that will move the pointer by the specified number of elements (i.e. by `number of elements * element.byteSize` bytes).

## Real life example

Now that we've covered all the basics, let's dive into a more involved example – using the `SHA1` function from `openssl`. It takes an input buffer of type `unsigned char*`, a `size_t` denoting the length of input and an output buffer of type `unsigned char*` and length 20.
Suppose you have a list of Luna `Int`s and want to compute the SHA1 digest of this list, as another list of `Int`s. This is how this can be done with Luna's FFI:

```
import Std.Foreign
import Std.Foreign.C.Value

def sha1Digest inputList:
    # Inputs preparation
    inputLength = inputList . length
    inBuf  = Pointer CUChar . mallocElems inputLength      # Allocate the input buffer.
    inSize = CSize.fromInt inputLength                     # Convert the length to a CSize.
    outBuf = Pointer CUChar . mallocElems 20               # Allocate the output buffer.
    indexed = 0 . upto inputLength . zip inputList
    indexed . each (ix, elem):
        inBuf . moveElems ix . write (CUChar.fromInt elem) # Write each element to the buffer at correct position.
        
    # Calling the foreign function
    sha1FunPtr = lookupSymbol "openssl" "SHA1"                          # Get the function from dynamic library.
    sha1FunPtr . call None [inBuf.toCArg, inSize.toCArg, outBuf.toCArg] # Call the function passing all the arguments
                                                                        # and specifying the return type as None
                                                                        
    # Getting the final results                                                                    
    result = 0 . upto 19 . each i:
        outBuf . moveElems i . read . toInt    # Read from the output buffer at consecutive positions
                                               # and convert the values back to Ints.
    
    # Cleanup
    inBuf.free    # Free the buffers.
    outBuf.free
    
    result
```