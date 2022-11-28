# FixedPoint64bit
An implementation of rapid fixed point arithmetic with 64 bit variables for storing fixed-point numbers in C.

## Objectives

The objective of this project is to implement a C library which satisfies four different criteria:
  1. It implements a datatype named `fixed`, which can store fractional numbers in fixed-point representation with 48 bits for storing the integer part and 16 bits for storing the fractional part.
  2. It implements basic arithmetic operations for this datatype using functions named `f_add`, `f_sub`, `f_mul` and `f_div`. These implementations should be as fast as possible.
  3. It implements the entire `math.h` API for this datatype, including functions such as `pow`, `sqrt`, `log`, `cos` etc. They may be renamed to `f_pow`, `f_sqrt` etc.
  4. It finally implements I/O for this datatype, allowing users to quickly parse strings into `fixed` variables and to return them to strings for printing back to the output or into a file.
  
## Philosophy
This project wishes to implement an API for accessing fixed point arithmetic using large memory words. We take a moment to consider why this needs to be done:
  - Existing libraries for working with fixed-point arithmetic use smaller `16.16` sizes for these numbers. A `16.16` fixed size means 16 bits for storing the integer part and 16 bits for storing the decimal part.
  - One way to get rapid fixed point math is to use COBOL, but COBOL is syntactically confounding for any programmer whose experience base is in the C-family of languages.
  - It is the year 2022, and high-level languages such as Python have implemented very, very good abstractions by which to write programs. The Zen of Python has established standards of abstraction that are so simple that a child could use it, and so transparent that an expert could optimize code with it. We want to implement such standards in the interface of a fixed-point library.
  - With modern C compilers, it is possible to have very optimized compilation. If the implementation is sufficiently simple, we can ensure very rapid execution of the code.
  - A great number of programmers have expressed distaste for the verbosity of Java, and verbosity in general is not very programmer friendly. Some of us are neither very quick with a keyboard, nor very comfortable with IntelliJ.

Taking all of these things into account, we decide upon the following objectives:
  1. As much as possible within the framework of a purely procedural language, our API should be *Pythonic*. It should prefer simple over complex, and explicit over implicit.
  2. Our API should not be verbose. It should be brief but lucid.
  3. Our implementation should be inline and quick as much as possible. It should be faster than floating point computations.
  4. It should not require programmers to think in a dramatically new way. Aside from the obvious constraints of using fixed point precision, the programmer should be able to use their past experience of working with numeric and mathematical libraries. Our interface should mimic `math.h` as much as possible.
