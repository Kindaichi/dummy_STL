# dummy STL

## A very brief introduction of STL
STL stands for Standard Template Library.

It is **standard**.(not third party,good third party libary may taken into the standard in the future)

It based on the **template** tech to make data structure friendly to any data types.

Of course, it came as a library support, mostly within the compiler package.You can find your c++ standard library in /usr/lib/ in most of the \*inux system.

Three major component in STL design.Container, iterator and algorithm.

Container: a template data struture to handle data access, delete, update etc.

algorithm: daily useful algorithm such as sort and find had been implemented. Algorithm works on data structure, in STL case, that is container. To make different algorithm work on different container, a middleware is required.

Iterator: This is the middleware betwwen algorithm and container.

## General Concept
This section is mostly learned from [The C++ Standard Library - A Tutorial and Reference](http://www.josuttis.com/libbook/)

- namespace
    ```cpp
    using namespace std
    ```
    - A namespace is a certain scope for identifiers
    - The code above is ok to use in small code. It makes all the identifiers in std available to you.But in complex code it might cause name clashes.

- Header files
    ```cpp
#include <cstdlib> //<stdlib.h>
#include <cstring> //<string.h>
    ```
    - use of namespace std for all identifiers in C++ standard libary is not backward compatible to old header fils.
    - new standard provide new header file, but also keep backward compatiable by allowing old header file to provide.(such as cstring and string.h)
    - In fact, old headers behave as if they declare all identifiers in namespace std followed by an explicit
    using declaration

- Error and Exception handling
    - different part of the library may have different design on exception handling.Such as string classes, support detailed error handling.Other parts, such as the STL (the standard template library) and valarrays, prefer
    **speed over safety**, so they rarely check for logical errors and throw exceptions only if runtime
    errors occur.
    - All exception has the same base class.Exception can be divided into three class:
        1. Exceptions for language support
            - bad_exception
            - bad_alloc
            - bad_cast
            - bad_typeid
        2. Exceptions for the C++ standard library
            - derived from logic_error, Logic errors are errors that, at least in theory, could be avoided by the program;
            - invalid argument
            - length_error
            - out_of_range
        3. Exceptions for errors outside the scope of a program
            - derived from runtime_error
            - range_error
- Allocators
    **TODO**

## Utilities
- pair
    - tempplate struct with two member: first and second
    - with compare utility
    - convenience: make_pair(0,1), but implicit conversion might happen
    - example: TODO

- auto_ptr
    - a smart pointer that helps to avoid **resource leaks** when exceptions are thrown
    - interface much like ordinary pointer(\*,->), but archmethic is not supported
    - Note that class auto_ptr<> does not allow you to initialize an object with an ordinary pointer by
    using the assignment syntax. Thus, you must initialize the auto_ptr directly by using its value
    - **DO NOT** initialize two auto_ptrs with the same object)
    - copy construct or assignment would transfer resource ownership!
    - so function call and fuction return would cause resource trasfer, note that constant auto_ptr reference is a good practice
    - auto_ptr as member can avoid construct exception(because deconstructor only called if constructor finish)
    - misuse
        - cant not share
        - cant not for array(delete rather than delete [])
        - auto_ptrs are not "universal smart pointers."
