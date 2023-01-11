# Move Semantics

An assignment will transfer ownership between variables:

```rust,editable
fn main() {
    let s1: String = String::from("Hello!");
    let s2: String = s1;
    println!("s2: {s2}");
    // println!("s1: {s1}");
}
```

* The assignment of `s1` to `s2` transfers ownership.
* The data was _moved_ from `s1` and `s1` is no longer accessible.
* When `s1` goes out of scope, nothing happens: it has no ownership.
* When `s2` goes out of scope, the string data is freed.
* There is always _exactly_ one variable binding which owns a value.

<details>

Key points: 
* With s1 & s2, if the ownership is not moved, when they both go out of scope, then there will be double free; see Figure 4-2 [here](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html).
* The "move" is similar to shallow copy in other languages, with the exception that the original variable becomes inactive. 
  * We say s1 was moved into s2.
* To get a deep copy you need to use “clone”

</details>
