# Shared and Unique Borrows

Rust puts constraints on the ways you can borrow values:

* You can have one or more `&T` values at any given time, _or_
* You can have exactly one `&mut T` value.

```rust,editable,compile_fail
fn main() {
    let mut a: i32 = 10;
    let b: &i32 = &a;

    {
        let c: &mut i32 = &mut a;
        *c = 20;
    }

    println!("a: {a}");
    println!("b: {b}");
}
```

<details>

Key notes:

* Unique mutable borrow
  * Prevents iterator invalidation
  * And situations like the [substring example](https://doc.rust-lang.org/book/ch04-03-slices.html)
  * In multi-threaded: Prevents data races at compile time

* Avoid dangling pointers: (**works better with String as the example**)
  * The compiler ensures that the data/value won’t go out of scope (is not freed) before all references are gone out of scope
  * This is done by keeping track of lifetimes.

</details>
