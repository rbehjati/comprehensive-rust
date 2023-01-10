# `String` vs `str`

We can now understand the two string types in Rust:

```rust,editable
fn main() {
    let s1: &str = "Hello";
    println!("s1: {s1}");

    let mut s2: String = String::from("Hello ");
    println!("s2: {s2}");
    s2.push_str(s1);
    println!("s2: {s2}");
}
```

Rust terminology:

* `&str` an immutable reference to a string slice.
* `String` a mutable string buffer.

<details>

* String literals are immutable string slices: “let hello_world: &'static str = "Hello, world!";”

* Could be on heap or stack or pre-allocated space in read-only memory.
    * where do you think "hello" is located in the memory? (stack, heap?)
    * where is the second string?
    
Try:
* Get a reference to s2.  
* Check length and capacity of s2, before and after push_str
* Show the documentation for str in std (see below)


More:
* String slices (or str) are what we work with when we either reference a range of UTF-8 text that is “owned” by someone else, or when we create them using string literals.
  
* [skip?] Static lifetime: string literals are guaranteed to be valid for the duration of the entire program.

* A &str is made up of two components: a pointer to some bytes, and a length .len() to get the length in bytes, not chars.

* Show the documentation for str in std

  * Recommend looking at it. Many handy functions.
  * Note as_bytes_mut only works on String not &str!
  * Cow: clone-on-write smart pointer
  * Trait Borrow is implemented for String
  * Raw strings and raw byte strings: they don’t process any scapes
</details>
