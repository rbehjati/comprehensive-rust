# Compound Types

|        | Types                         | Literals                          |
|--------|-------------------------------|-----------------------------------|
| Arrays | `[T; N]`                      | `[20, 30, 40]`, `[0; 3]`          |
| Tuples | `()`, `(T,)`, `(T1, T2)`, ... | `()`, `('x',)`, `('x', 1.2)`, ... |

Array assignment and access:

```rust,editable
fn main() {
    let mut a: [i8; 10] = [42; 10];
    a[5] = 0;
    println!("a: {:?}", a);
}
```

Tuple assignment and access:

```rust,editable
fn main() {
    let t: (i8, bool) = (7, true);
    println!("1st index: {}", t.0);
    println!("2nd index: {}", t.1);
}
```

<details>

These have known size at compile time and are stack allocated.

Note on formatting:

 * ':' is used to ask for a special formatting. You can see the full grammar [here](https://doc.rust-lang.org/std/fmt/#syntax). 
 * Display vs Debug formatting.
 * There is the `dbg!` macro, but it prints to error, which is not captured in the playground.
 
</details>
