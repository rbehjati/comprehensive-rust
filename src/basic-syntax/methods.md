# Methods

Rust has methods, they are simply functions that are associated with a particular type. The
first argument of a method is an instance of the type it is associated with:

```rust,editable
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }

    fn inc_width(&mut self, delta: u32) {
        self.width += delta;
    }
}

fn main() {
    let mut rect = Rectangle { width: 10, height: 5 };
    println!("old area: {}", rect.area());
    rect.inc_width(5);
    println!("new area: {}", rect.area());
}
```

* We will look much more at methods in today's exercise and in tomorrow's class.

<details>

* Note the . syntax. 
* Note the we did not have to declare the variable as a reference. This happens on methods, but not ordinary functions. 
* If there is a question about replacing the receiver type with "self", say that the method is then called "consuming", and you won't be able to use the object any more after that point. We will come back to that in the afternoon.
</details>
