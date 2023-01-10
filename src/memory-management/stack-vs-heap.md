# The Stack vs The Heap

* Stack: Continuous area of memory for local variables.
  * Values have fixed sizes known at compile time.
  * Extremely fast: just move a stack pointer.
  * Easy to manage: follows function calls.
  * Great memory locality.

* Heap: Storage of values outside of function calls.
  * Values have dynamic sizes determined at runtime.
  * Slightly slower than the stack: some book-keeping needed.
  * No guarantee of memory locality.
  
  
<details>
More reading:

* All data stored on the stack must have a fixed known size.
* [Stack & heap]( https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/book/first-edition/the-stack-and-the-heap.html)
</details>
