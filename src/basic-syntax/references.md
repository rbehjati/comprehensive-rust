# References

Like C++, Rust has references:

```rust,editable
fn main() {
    let mut x: i32 = 10;
    let ref_x: &mut i32 = &mut x;
    *ref_x = 20;
    println!("x: {x}");
}
```

Some differences from C++:

* We must dereference `ref_x` when assigning to it, similar to C pointers,
* Rust will auto-dereference in some cases, in particular when invoking
  methods (try `count_ones`).
* References that are declared as `mut` can be bound to different values over their lifetime.

<details>

* Reference: similar to a pointer (address to follow to access data/value); but is guaranteed to point to an existing value of a known type. 

* These ampersands represent references, and they allow you to access some value (without taking ownership of it). 

* We call the action of creating a reference borrowing (as opposed to owning the data/value). Very useful in function calls. 
  
  * **Variable x owns the value 10, but variable ref_x does not own the value; only borrows it (has a reference to value 10).**

* The opposite of referencing by using & is dereferencing, which is accomplished with the dereference operator, *.

</details>
