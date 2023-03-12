# Deriving Traits

You can let the compiler derive a number of traits:

```rust,editable
#[derive(Debug, Clone, PartialEq, Eq, Default)]
struct Point {
    x: i32,
    y: i32,
}


fn main() {
    let p1 = Point::default();
    let p2 = p1.clone();
    println!("Is {:?}\nequal to {:?}?\nThe answer is {}!", &p1, &p2,
             if p1 == p2 { "yes" } else { "no" });
}
```
