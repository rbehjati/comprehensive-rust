# Lifetimes

A borrowed value has a _lifetime_:

* The lifetime can be elided: `add(p1: &Point, p2: &Point) -> Point`.
* Lifetimes can also be explicit: `&'a Point`, `&'document str`.
* Read `&'a Point` as "a borrowed `Point` which is valid for at least the
  lifetime `a`".
* Lifetimes are always inferred by the compiler: you cannot assign a lifetime
  yourself.
  * Lifetime annotations create constraints; the compiler verifies that there is
    a valid solution.

<details>

* All references have a lifetime.
* Lifetimes can be elided [ref](https://doc.rust-lang.org/book/ch10-03-lifetime-syntax.html#lifetime-elision):
  * Some lifetime patterns are overwhelmingly common (and deterministic) and so the borrow checker will allow you to omit them to save typing and to improve readability. This is known as elision. Elision exists in Rust solely because these patterns are common.
  * The borrow checker applies 3 rules; 1 on input, 2 on output. If it cannot infer lifetimes with those rules, then you have to provide lifetime annotations.
  * Most of the time, an error message suggesting the 'static lifetime results from attempting to create a dangling reference or a mismatch of the available lifetimes.
* Explicit annotation [example](https://doc.rust-lang.org/rust-by-example/scope/lifetime/explicit.html).


The static lifetime:

* A 'static lifetime is the longest possible lifetime, and lasts for the lifetime of the running program. A 'static lifetime may also be coerced to a shorter lifetime. 
* Two ways to make a variable with 'static lifetime, and both are stored in the read-only memory of the binary.
* As a trait bound, it means the type does not contain any non-static references.
</details>
