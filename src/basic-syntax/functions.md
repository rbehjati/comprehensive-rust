# Functions

A Rust version of the famous [FizzBuzz](https://en.wikipedia.org/wiki/Fizz_buzz) interview question:

```rust,editable
fn main() {
    fizzbuzz_to(20);   // Defined below, no forward declaration needed
}

fn is_divisible_by(lhs: u32, rhs: u32) -> bool {
    if rhs == 0 {
        return false;  // Corner case, early return
    }
    lhs % rhs == 0     // The last expression is the return value
}

fn fizzbuzz(n: u32) -> () {  // No return value means returning the unit type `()`
    match (is_divisible_by(n, 3), is_divisible_by(n, 5)) {
        (true,  true)  => println!("fizzbuzz"),
        (true,  false) => println!("fizz"),
        (false, true)  => println!("buzz"),
        (false, false) => println!("{n}"),
    }
}

fn fizzbuzz_to(n: u32) {  // `-> ()` is normally omitted
    for n in 1..=n {
        fizzbuzz(n);
    }
}
```

<details>

Key points:

* Statements are instructions that do something, they don't return a value. Expressions evaluate to a value, they return that value. 
* The match expression: create a tuple on the fly. This is a useful pattern.
* Note the range: 1..=n.
* Possibly mention [const](https://doc.rust-lang.org/std/keyword.const.html) function: compile-time evaluable functions.
</details>
