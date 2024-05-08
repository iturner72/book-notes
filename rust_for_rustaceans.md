# Rust for Rustaceans

by Jon Gjengset 

*I, Ian Turner own this book and took these notes for my own learning, purchase
the book here: *https://www.amazon.com/Rust-Rustaceans-Programming-Experienced-Developers/dp/1718501854*

## Chapter 1: Foundations 

* 5 There are many different regions of memory, and perhaps surprisingly, not
  all of them are stored in the DRAM of your computer. Which part of memory you
  use has a significant impact on how you write your code. The three most
  important regions for the purposes of writing Rust code are the stack, the
  heap, and static memory.

* 5 The *stack* is a segment of memory that your program uses as scratch space
  for function calls. Each time a function is called, a contiguous chunk of
      memory called a *frame* is allocated at the top of the stack. Near the
      bottom of the stack is the frame for the main function, and as functions
      call other functions, additional frames are pushed onto the stack. A
      function's frame contains all the variables within that function, along
      with any arguments the functions takes. When the function returns, its
      stack frame is reclaimed.

* 6 The *heap* is a pool of memory that isn't tied to the current call stack of
  the program. Values in heap memory live until they are explicitly deallocated.
  This is useful when you want a value to live beyond the lifetime of the
  current function's frame. If that value is the function's return value, the
  calling function can leave some space on its stack for the called function to
  write that value into before it returns. But if you want to, say, send that
  vale to a different thread with which the current thread may share no stack
  frames at all, you can store it on the heap.

* 6 The primary mechanism for interacting with the heap in Rust is the Box type.
  When your write Box::new(value), the value is placed on the heap, and what
  your are given back (the Box<T>) is a pointer to that value on the heap. When
  the Box is eventually dropped, that memory is freed. If you forget to
  deallocate heap memory, it will stick around forever, and your application
  will eventually eat up all the memory on your machine. This is called *leaking
  memory* and is usually something you want to avoid. However, say you have a
  read-oly configuration that the entire program should be able to access. You
  can allocate that on the heap and explicitly leak it with Box::leak to get a
  'static reference to it.

* 6 *Static memory* is really a catch-all term for serveral closely related
  regions located in the file you program is compiled into. These regions are
  automatically loacec into your program's memory when that program is executed.
  Values in static memory live for the entire execution of your program. Your
  program's static memory contains the program's bimary code, which is usually
  mapped as read-only. As your program executes, it walks through the binary
  code in the text segment instruction by instruction and jumps around whenever
  a function is called. Static memory also holds the memory for variables you
  declare with the static keyword, as well as certain constant values in your
  code.

* 7 Rust's memory model centers on the idea that all values have a single
  *owner* &mdash; that is, exactly one location (usually a scope) is responsible
  for ultimately deallocating each value. This is enforced through the borrow
      checker. If the value is moved, such as by assigning it to a new variable
      pushing it to a vector, or placing it on the heap, the ownership of the
      value moves from the old location to the new one. At that point, you can
      no longer access the value through variables that flow from the original
      owner, even though the bits that make up the value are technically still
      there. Instead, you must access the moved value through variables that
      refer to its new location.

* 9 Rust allows the owner of a value to lend out that value to others, without
  giving up ownership, through references. *References* are pointers that come
  with an additional contract for how they can be used, such as whether the
  reference proides exclusive access to the referenced value, or whether the
  referenced value may also have other references point to it.

* 9 A shared reference, &T, is, as the name implies, a pointer that may be
  shared. Any number of other references may exist to the same value, and each
  shared reference is Copy, so you can trivially make more of them. Values
  behind shared references are not mutable; you cannot modify or reassign the
  value a shared reference points to, nor can you cast a shared reference to a
  mutable one.

* 10 The alternative to a shared referene is a mutable reference: &mut T. With
  mutable references, the Rust compiler is again allowed to make full use of the
  contreact that the reference comes with: the ocmpiler assues that there are no
  other threads accessing the target value, whether through a shared reference
  or a mutable one. In other words, it assumes that the mutable reference is
  *exclusive*. This enables some interesting optimizations that are not readily
  available in other languages.

* 12 Some types frovide *interior mutability*, meaning they allow you to mutate
  a value through a shared reference> These types usually rely on additional
  mechanisms (like atomic CPU instructions) or invariants to provide safe
  mutability without relying on the semantics of exclusive references. These
  normally fall into two categories: those that let you get a mutable reference
  through a shared reference, and those that let your replace a value given only
  a shared reference. The first category consists of types lie Mutex and
  RefCell, which cintain safety mechanisms to ensure that, for any value they
  give a mutable reference to, only one mutable reference (and not ashared
  references) can exists at a time. Under the hood, they types (and those like
  them) all rely on a type called UnsageCell, whose name should immediately make
  you hesitate to use it. We will cover UnsafeCell in more detail in Chapter 8,
  but for now you should knowo that it is the *only* correct way to mutate
  through a shared reference.

* 13 At the heart of Rust lifetimes is the *borrow checker*. Whenever a
  reference with some lifetime 'a is used, the borrow checker checks that 'a is
  still *alive*. It does this by tracing the path back to where 'a starts
  &mdash; where the reference was taken &mdash; from the point of use and
  checking that there are no conflicting uses along that path. This ensures that
  the reference still points to a value that is safe to access. This is similar
  to the high-level "data flow" mental model we discussed earlier in the
  chapter; the comiler checks that the flow of th reference we are accessing
  does not confict with any other paralledl flows.

* 15 Variance is a concept that programmers are often exposed to but rarely know
  the name of because it's mostly invisible. At a glance, variance describes
  what types are subty[es of other types and when a subtype can be used in place
  of a supertype (and vice versa). Broadly speaking, a type A is a subtype of
  another type B if A is at least as useful as B. Variance is the reason why, in
  Java, you can pass a Turtle to a function that accepts an Animal if Turtle is
  a subtype of Animal, or why, in Rust, you can pass a &'static str to a
  function that accepts a &'a str.

* 16 All types have a variance, which defines what other simllar types can be
  used in that type's place. There are three kinds of variance: covariant,
  invariant, and contravariant. A type is *covariant* if you can just use a
  subtype in place of the type. For example, if a variable is of type &'a T, you
  can provide a value of type &'static T to it, because &'a T is covariant in
  'a. &'a T is also covariant in T, so you can pass a &Vec<&'static str> to a
  function that takes &Vec<&'a str>. Some types are *invariant*, which means
  that you must provide exactly the given type. &mut T is an example of this
  &mdash; if a function takes a &mut Vec<&'a str> you cannot pass it a &mut
  Vec<&'static str>. That is, &mut T is invariant in T. If you could, the
  function could put a short-lived string inside the Vec, which the caller would
  then continue using, thinking that were a Vec<&'static str> and thus that the
  contained string were 'static! Any type that provides mutability is generally
  invariant for the same reason &mdash; for example, Cell<T> is invariant in T.
  The last category, *contravariance*, comes up for function arguments. Function
  types are more useful if they're okay with their arguments being *less*
  useful. This is clearer if you contrast the variance of the argument types on
  their own with thier variance when used as funciton arguments.


## Chapter 2: Types

* 20 Before we talk about how a type's in-memory representation is determined,
  we first need to descuss the notion of *alignment*, which dictates where the
  bytes for a type can be stored.

* 23 Sometimes, you want to give a particular field or type a larger alignment
  than it technically requires. You can do that using the attribute
  #[repr(align(n))]. A common use case for this is to ensure that different
  values stored contiguously in memory (like in an array) end up in defferent
  cache lines on the CPU. That way, you avoid *false sharing*, which can cause
  huge performance degradations in concurrent programs. False sharing occurs
  when two different CPUs access different values that happen to share a cache
  line; while they can theorietically operate in parallel, they both end up
  contending to update the same single entry in the cache. We'll talk about
  concurrency in much greater detail in Chapter 10.

* 24 Traits are a kye piece of Rust's type system &mdash; they are the glue that
  allows types to interoperate even though they don't know about each other at
  the time they are defined. By now, you've probably written a decent amount of
  generic code in Rust. You/ve used generic type parameters on types and
  methods, and maybe even a few trait bounds here and there. But have you ever
  wondered what actually happens to generic code when you compile it, or what
  happens when you call a trait method on a dyn Trait? When you write a type or
  function that is generic over T, you're really telling the compiler to make a
  copy of that type or function for each type T. When you construct a Vec<i32>
  or a HashMap<String, bool>, the compiler essentially copy-pastes the generic
  type and all its implementation blocks and replaces all instances of each
  generic parameter with the concrete type you provided.

* 25 This process of going from a generic type to many non-generic types is
  called *monomorphization*, and it's part of the reason generic Rust code
  usually performs just as well as non-generic code. By the time the compiler
  starts optimizing your code, it's as if no generics were there at all!
  Monomorphization also comes at a cost: all those instantiations of your type
  need to be compiled separately, which can increate compile time if the
  compiler cannot optimize them away. Each monomorphized function also results
  in its own chunk of machine code, which can make your program larger. And
  because instructions aren't shared between different instantiations of a
  generic type's methods, the CPU's instruction cache is also less effective as
  it now needs to bold multiple copies of effectively the same instructions.

* 26 The alternative to static dispatch is *dynamic dispatch*, which enables
  code to call a trait method on a generic type without knowing what the type
  is. Dynamic dispathc cuts copmile times, since it's no longer necessary to
  compile multiple copies of types and methods, and it can improve the
  efficiency of your CPU instruction cache. However, it also prevents the
  compiler from optimizing for the specific types that are used.

* 28 When you're given the choice between static and dynamic dispatch, there is
  rarely a clear-cut right answer. Broadly speaking, though, you'll want to use
  static dispatch in your libraries and dynamic dispatch in your binaries.

* 29 Rust has some fairly strict rules about where you can implement traits and
  what types you can implement them on. These rules exist to preserve the
  *coherence* property: for any given type and method, there is only ever one
  correct choice for which implementation of the method to use for that type.

* 29 In Rust, the rule that established that balance is the *orphan rule*.
  Simply stated, the orphan rule says that you can implement a trait for a type
  only if the trait *or* the type is local to your crate. So, you can implement
  Debug for your own type, and you can implement MyNeatTrait for bool but you
  cannot implement Debug for bool. If you try, your code will not copmile, and
  the compiler will tell you that there are conflicting implementations.

* 31 The standard library is flush with trait bounds, whether it's that the keys
  in a HashMap must implement Hash + Eq or that the function given to
  thread::spawn must be FnOnce + Send + 'static. When you write generic code
  yourself, it will almost certainly include trait bounds, as otherwise your
  code cannot do much with the type it is generic over. As you write more
  elaborate generic implementations, you'll find that you also need more
  fidelity from your trait bounds, so let's look at some of the ways to achieve
  that.

* 31 ...if your method wants to contstruct a HashMap<K, V, S> whose keys are
  some generic type T and whose value is a usize, instead of writing the bounds
  out like where T: Hash + Eq, S: BuildHasher + Default, you could write where
  HashMap<T, usize, S>: From Iterator. This saves you from looking up the exact
  bounds requirements for the mothods you end up using and more clearly
  communicates the "true" requirement of your code. As you can see, it can also
  significantly reduce the complexity of your bounds if the bounds on the
  underlying trait methods you want to call are complex.

## Chapter 3: Designing Interfaces
