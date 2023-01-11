# Static and Constant Variables

Global state is managed with static and constant variables.

## `const`

You can declare compile-time constants:

```rust,editable
const DIGEST_SIZE: usize = 3;
const ZERO: Option<u8> = Some(42);

fn compute_digest(text: &str) -> [u8; DIGEST_SIZE] {
    let mut digest = [ZERO.unwrap_or(0); DIGEST_SIZE];
    for (idx, &b) in text.as_bytes().iter().enumerate() {
        digest[idx % DIGEST_SIZE] = digest[idx % DIGEST_SIZE].wrapping_add(b);
    }
    digest
}

fn main() {
    let digest = compute_digest("Hello");
    println!("Digest: {digest:?}");
}
```

## `static`

You can also declare static variables:

```rust,editable
static BANNER: &str = "Welcome to RustOS 3.14";

fn main() {
    println!("{BANNER}");
}
```

We will look at mutating static data in the [chapter on Unsafe Rust](../unsafe.md).

<details>
Try:

* Static: similar to const but static items aren’t inlined upon use. This means that there is only one instance for each value, and it’s at a fixed location in memory.
* Make BANNER string.
* Remove its type: Unlike let bindings, you must annotate the type of a static.
* The type of a static value must be Sync unless the static value is mutable.
* Static variables have a 'static lifetime.
* Check `wrapping_add` in the docs.
</details>
