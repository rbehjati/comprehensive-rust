# Memory Management in Rust

Memory management in Rust is a mix:

* Safe and correct like Java, but without a garbage collector.
* Scope-based like C++, but the compiler enforces full adherence.
* Has no runtime overhead like in C and C++.

It achieves this by modeling _ownership_ explicitly.

<details>

Key points: 
* Rust’s most unique feature 
* Allows memory safety guarantees without needing a garbage collector
  * “knowing that the main purpose of ownership is to manage heap data can help explain why it works the way it does”
* Rules: 
  * Each value has an owner (e.g., a variable)
  * There can only be one owner at a time.
  * The the owner goes out of scope the value is dropped. 
</details>
