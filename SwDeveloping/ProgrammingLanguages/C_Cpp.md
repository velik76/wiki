# Table of Contents

- [Table of Contents](#table-of-contents)
  - [X-Macros](#x-macros)
  - [Lambdas](#lambdas)
  - [C tipps](#c-tipps)

## X-Macros

The most common use of X Macros() is for associating error text with error codes. When new error codes are added, programmers must remember to add the code and the text, typically in separate places. The X Macro allows the new error data to be added in a single place and get automatically populated anywhere it is needed.

See further infos with examples on [Link](http://stackoverflow.com/questions/264269/what-is-a-good-reference-documenting-patterns-of-use-of-x-macros-in-c-or-possib)

## Lambdas

[Link](http://www.dreamincode.net/forums/topic/264061-c11-fun-with-functions/) And this one [Link](http://www.cprogramming.com/c++11/c++11-lambda-closures.html) are usefull

- []: no variables defined. Attempting to use any external variables in the lambda is an error.
- [x, &y]: x is captured by value, y is captured by reference
- [&]: any external variable is implicitly captured by reference if used
- [=]: any external variable is implicitly captured by value if used
- [&, x]: x is explicitly captured by value. Other variables will be captured by reference
- [=, &z]: z is explicitly captured by reference. Other variables will be captured by value
- [this]: Capture the this pointer of the enclosing class

## C tipps

[Some useful tipps](https://matt.sh/howto-c)
