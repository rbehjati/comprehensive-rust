# Lifetimes in Data Structures

If a data type stores borrowed data, it must be annotated with a lifetime:

```rust,editable
#[derive(Debug)]
struct Highlight<'doc>(&'doc str);

fn erase(text: String) {
    println!("Bye {text}!");
}

fn main() {
    let text = String::from("The quick brown fox jumps over the lazy dog.");
    let fox = Highlight(&text[4..19]);
    let dog = Highlight(&text[35..43]);
    // erase(text);
    println!("{fox:?}");
    println!("{dog:?}");
}
```

<details>

* `<'doc>`:  They spread around and infect the code.
  * Try not to have them. Unless it really need to reference data, because you cannot get rid of them. 
  * Restriction on the caller: first the reference must go out of scope, then then caller can go.
  * In this case you could instead use an owned "String".
    * Whether this is acceptable or not performance-wise depends on your use case.
* erase: take ownership of the string
* You cannot move out a variable if it is borrowed.   
* comment out the `println!` lines. The erase should work fine. 
</details>
