# Programming Rust

by Jim Blandy, Jason Orendorff, and Leonora F.S. Tindall

*I, Ian Turner own this book and took these notes for my own learning, purchase
the book here: https://www.amazon.com/Programming-Rust-Fast-Systems-Development/dp/1492052590*

## Chapter 1: System Programmers Can Have Nice Things 

* 3 The Rust language makes you a simple promise: if your program passes the
  compiler's checks, it is free of undefined behavior. Dangling pointers,
  double-frees, and null pointer dereferences are all caught at compile time.
  Array references are secured with a mix of compile-time and run-time checks,
  so there are no buffer overruns: the Rust equivalent of our unfortunate C
  program exits safely with an error message. 

## Chapter 2: A Tour of Rust

* 12 Rust's growable vector type, analogous to C++'s std:vector, a Python list,
  or a Java Script array. Even thoug hvectors are designed to be ghrown and
  shrunk dynamically, we must still mark the variable mut for Rust to let us
  push numbers onto the end of it.

* 14 So when we iterate, we want to tell Rust that *ownership* of the vector
  should remain with numbers; we are merely *borrowing* its elements for the
  loop. The & operator in &numbers[1..] borrows a *reference* to the vocor's
  elements from the second onward. The for loop iterates over the referenced
  elements, letting m borror each emement in succession. The * operator in *m
  *dereferences* m, yielding the value it refers to; this is the next u64 we
  want to pass to gcd. Finally, since numbers owns the vector, Rust
  automatically frees it when numbers goes out of scope at the end of main.

* 39 Here we decide to use eight threads... Here we divide the pixel buffer into
  bands. The buffer's chunks_mut method returns an iterator producing mutable,
  nonoverlapping slices of the buffer, each of which encloses rows_per band *
  bounds.0 pixels-- in other words, rows_per_band complete rows of pixels... THe
  argument |spawner| { ... } is a Rust closure that expects a single argument,
  spawner. In this case, crossbeam::scope calls the closure, passing as the
  spawner argument a value the closure can use to create new threads. The
  crossbeam::scope function waits for all such threads to finish execution
  before returning itself.

* 42 Rust has found a significant niche in the world of command-line tools. As a
  modern safe, and fast systems programming language, it gives programmers a
  toolbox they can use to assemble slick command-line interfaces that replicate
  or extend the functionality of existing tools. For instance, the bat command
  provides a syntax highlighting-aware cat alternative with build-in support for
  paging tools, and hyperfine can automatically benchmark anything that can be
  run with a command or pipeline.

## Chapter 3: Fundamental Types 

* 49 To a great extent, the Rust language is designed around its types. Its
  support for high performance code arises from letting developers choose the
  data representation that best fits the situation, with the right balance
  between simplicity and cost. Rust's memory and thread safety guarantees also
  rest on the soundness of its types system, and Rust's flexibi9lity stems from
  its generic types and traits. ...Compared to a dynamically typed language like
  JavaScript or Pyhthon, Rust requires more planning from you up front. You must
  spell out the types of function arguments and return values, struct fields,
  and a few other constucts. However, two features of Rust make this less
  throuble than you might expect:

  * Given the types that you do spell out, Rust's *type inference* will figure
    out most of the rest for you. In practice, there's often only one type that
    will work for a given variable or expression; when this is the case, Rust
    lets you leave out, or *elide*, the type.
  * Functions can be *generic*: a single function can work on values of many
    different types. In Python and JavaScript, all functions work this way
    neturally: a function can operate on any valye that has the properties and
    methods the function will need. But it's exactly this flexibility that makes
    it so difficult for those languages to detect type errors early; testing is
    often the only way to catch such mistakes. Rust's generic functions give the
    language a degree of the same flexibility, while still catching all type
    errors at compile time.

  * 56 When an integer arithmetic operation overflows, Rust panics, in a debug
    build. In a release build, the operation *wraps around*: it produces the
    valuye equivalent to the mathematically correct result modulo the range of
    the value. ...These integer arithmetic methods fall in four general
    categories:

    * *Checked* operations return an Option of the result: Some(v) if the
      mathematically correct result can be represented as a value of thay type,
      or None if it cannot.
    * *Wrapping* operations return the value equivalent to the mathematically
      correct result modulo the range of the value:
    * *Saturating* operations return the representable value that is closest to
      the mathematically correct result. In other words, the result is "clamped"
      to the maximum and minimum values the type can represent.
    * *Overflowing* operations return a tuple (result, overflowed), where result
      is what the wrapping version of the function would return, and overflowed
      is a bool indicating whether an overflow occurred.

* 65 Rust has several types that represent memory addresses. This is a big
  difference between Rust and most languages with garbage collection. The good
  news in that the pointer types used in safe Rust are constrained to eliminate
  undefined behavior, so pointers are much easier to use correctly in Rust than
  in C++. We'll discuss three pointer types here: references, boxes, and unsafe
  pointers. A value of type &String (pronounced "ref String") is a reference to
  a String value, a &i32 is a reference to an i31, and so on.

* 66 The simplest way to allocate a value in the heap is to use Box::new: The
  call to Box::new allocates enough memory to contain the typle on the heap.
  When b goes out of scope, the memory is freed immediately, unless b has been
  *moved*-- by returning it, for example.

* 66 Rust also has the raw pointer types *mut T and *const T. Raw pointers
  really are just like pointers in C++. Using a raw pointer is unsafe, because
  Rust makes no effort to track what it points to. For example, raw pointers may
  be null, or they may point to  memory that has been freed or that now contains
  a value of a different type. All the classic pointer mistakes of C++ are
  offered for your enjoyment. 

* 67 Rust has three types for representing a sequence of values in memory:

  * The type [T; N] represents an array of N values, each of type T. An array's
    size is a constant determined at compile time and is part of the type; you
    can't append new elements or shrink an array.
  * The type Vec<T>, called *vector of Ts*, is a dynamically allocated, growable
    sequence of values of type T. A vector's elements live on the heap, so you
    can resize vectors at will: push new elements onto them, append other
    vectors to them, delete elements, and so on.
  * The types &[T] and &mut [T], called a *shared slice of Ts* and *mutable
    slice of Ts*, are references to a series of elements that are a part of some
    other value, like an array or vector. You can think of a slice as a pointer
    to its first element, together with a count of the number of elements you
    can access starting at that point. A mutable slice &mut [T] lets you read
    and modify elements, but can't be shared; a shared slice &[T] lets you share
    access among several readers, but doesn't let you modify elements.
