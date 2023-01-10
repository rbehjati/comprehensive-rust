# Day 1: Morning Exercises

In these exercises, we will explore two parts of Rust:

* Implicit conversions between types.

* Arrays and `for` loops.

<details>

Notes:

* We have two exercises; and 45 mins. The first one is smaller, so perhaps do it in 10-15 mins.

* From & into: A duality between From and Into (prefer implementing From over Into) 
  * U from T == T into U; We implement the former and automatically get the into version, thanks to the blanket implementation in the standard lib.
  * If you need T from U; you have to implement it separately. 
  * There is also TryFrom and TryInto. The same duality and blanket implementation exists here too.
* What is the difference between “as <type>” and “<var>.try_into().unwrap()”?
  * `as` is known to the compiler to work in certain situations (for certain conversions) 
  





A few things to consider while solving the exercises:

* Use a local Rust installation, if possible. This way you can get
  auto-completion in your editor. See the page about [Using Cargo] for details
  on installing Rust.

* Alternatively, use the Rust Playground.

The code snippets are not editable on purpose: the inline code snippets lose
their state if you navigate away from the page.

[Using Cargo]: ../../cargo.md

</details>
