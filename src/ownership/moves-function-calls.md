# Moves in Function Calls

When you pass a value to a function, the value is assigned to the function
parameter. This transfers ownership:

```rust,editable
fn say_hello(name: String) {
    println!("Hello {name}")
}

fn main() {
    let name = String::from("Alice");
    say_hello(name);
    // say_hello(name);
}
```

<details>

* How could we change this so that we could call `say_hello` again?
* What if we used `&str` instead?
* Actually, using `&str` is more generic. (auto deref)
* The other alternative (which does not work for String, because internally it use Vec which implements Drop) is to make your type `Copy`.

* Note: In a way everything in Rust is pass by value.
* Note: It is not possible to move if the type is copy.
</details>
