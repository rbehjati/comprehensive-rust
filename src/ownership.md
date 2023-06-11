# Ownership

[Ownership rules](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html):

* Each value in Rust has an _owner_ (a variable).
  * Each variable has a scope.
* There can only be one owner at a time.
* When the owner goes out of scope (at the end of the scope), the value will be dropped.
    * This frees the allocated memory. 
    * A destructor can run here to free up resources.


```rust,editable,compile_fail
struct Point(i32, i32);

fn main() {
    {                               // variable not valid yet, it’s not yet declared
        let p = Point(3, 4);        // variable is valid from this point forward
        println!("x: {}", p.0);
    }                               // scope is over; variable is no longer valid
    println!("y: {}", p.1);
}
```
