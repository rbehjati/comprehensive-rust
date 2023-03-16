# `Arc`

[`Arc<T>`][1] allows shared read-only access via its `clone` method:

```rust,editable
use std::thread;
use std::sync::Arc;

fn main() {
    let v = Arc::new(vec![10, 20, 30]);
    let mut handles = Vec::new();
    for _ in 1..5 {
        let v = v.clone();
        handles.push(thread::spawn(move || {
            let thread_id = thread::current().id();
            println!("{thread_id:?}: {v:?}");
        }));
    }

    handles.into_iter().for_each(|h| h.join().unwrap());
    println!("v: {v:?}");
}
```

[1]: https://doc.rust-lang.org/std/sync/struct.Arc.html

<details>

* `Arc` stands for "Atomic Reference Counted", a thread safe version of `Rc` that uses atomic
  operations.
* `Arc<T>` implements `Clone` whether or not `T` does. It implements `Send` and `Sync` iff `T`
  implements them both.
* `Arc::clone()` has the cost of atomic operations that get executed, but after that the use of the
  `T` is free.
* What did we gain here by using `Arc`? Try removing `Arc`:
  * What does `println!("{thread_id:?}: {:p}", &v);` print when you don't have Arc?
  * How about `println!("{thread_id:?}: {:p}", v, {:p}", &v);` when you have Arc?
  * Benefit of using Arc:
    * If Vec is too large: without Arc you get a performance & memory overhead with all the cloning.
    * If the inner type T is not clone, you need Arc.
* Rewrite with `thread::scope(|s| {`.
* Beware of reference cycles, `Arc` does not use a garbage collector to detect them.
    * `std::sync::Weak` can help.

</details>
