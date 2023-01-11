# Type Inference

Rust will look at how the variable is _used_ to determine the type:

```rust,editable
fn takes_u32(x: u32) {
    println!("u32: {x}");
}

fn takes_i8(y: i8) {
    println!("i8: {y}");
}

fn main() {
    let x = 10;
    let y = 20;

    takes_u32(x);
    takes_i8(y);
    // takes_u32(y);
}
```

<details>

Try:

* Add a vec declaration, to show the use of `_` in type specification. 
     ```
      let v: Vec<_> = Vec::new(); 

      // let mut v: Vec<_> = Vec::new(); 
      // v.push(2);
     ``` 
* More interesting: 

    ```
    let v2 = v.iter().collect(); // cannot infer type.
    let m = v.iter().collect::<Vec<_>>();
    let m = v.iter().enumerate().collect::<std::collections::HashMap<_,_>>();
    ```

* Type inference happens at function boundaries. 
  * Functions must fully specify parameter types in the signature.
  * Give better error messages, and faster compilation.
 
</details>
