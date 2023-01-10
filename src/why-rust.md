# Why Rust?

Some unique selling points of Rust:

* Compile time memory safety.
* Lack of undefined runtime behavior.
* Modern language features.

<details>

Make sure to ask the class which languages they have experience with. Depending
on the answer you can highlight different features of Rust:

* Experience with C or C++: Rust eliminates a whole class of _runtime errors_
  via the borrow checker. You get performance like in C and C++, but you don't
  have the memory unsafety issues. In addition, you get a modern language with
  constructs like pattern matching and built-in dependency management

  * Because C was designed to be an “extremely efficient low-level programming language” [[1]](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html).
  * Some undefined behaviour (that allow optimization [[1]](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html))
    * Uninitialized variable 
    * Integer overflow 
    * Dereference wild pointers (e.g., double free, out of bound array access)
    * Pointer casts
  * Some optimizations cause security issues [[2]](https://blog.llvm.org/2011/05/what-every-c-programmer-should-know_14.html)


* Experience with Java, Go, Python, JavaSript...: You get the same memory safety
  as in those languages, plus a similar high-level language feeling. In addition
  you get fast and predictable performance like C and C++ (no garbage collector)
  as well as access to low-level hardware (should you need it)

</details>
