# Contexts

While it is interesting to study programs that perform all their computations without the connection to the outside world, more often than not we need to interact with some external resources (even if it's just a file locally stored on a laptop). In this section we introduce Contexts – Luna's basic facility for dealing with interactions with the outside world and providing ways to modify the way the program is executed.

## Why bother?

The notion of contexts may seem superficial at first glance. Why do we even need them? The most popular languages in the world use IO operations, exceptions, mutable memory etc. without ever bounding those to such "Contexts". It is, however, very beneficial for the safety and performance of programs and, when implemented right, does not burden the programmer with layers of cognitive load.

First of all, containing the so–called "side effects" in contexts results in less bugs – you will never throw an error, modify a memory area or make an HTTP request unnoticed. Every time you interact with the outside world or change the semantics of a program (as is the case with throwing errors), the compiler knows it and displays the information in an accessible form. It also allows the compiler to automatically parallelize your code – it is a safe operation only when the particular section of code does not interact with the outside world. Thus the compiler needs a way to recognize such sections.

Moreover, having the effects explicitly described on type level gives a much greater degree of their execution to the programmer. Since effectful computations are first-order and well-typed citizens of the language, you may decide to delay the effects, run such computations multiple times etc.

## Effectful values

