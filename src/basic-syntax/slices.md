# Slices

A slice gives you a view into a larger collection:

```rust,editable
fn main() {
    let a: [i32; 6] = [10, 20, 30, 40, 50, 60];
    println!("a: {a:?}");

    let s: &[i32] = &a[2..4];
    println!("s: {s:?}");
}
```

* Slices borrow data from the sliced type.
* Question: What happens if you modify `a[3]`?

<details>

Slice: Borrowed/Reference to a subset/section of an array
* Note the **type signature** &[T].
* Section/subset is specified by a range of the form [starting_index..ending_index]
* Does not have compile-time specified length/size
* A slice is a two-word object, the first word is a pointer to the data, and the second word is the length of the slice.


Try:
* other ranges ([..2], [2..], [..] (gives you the entire array as a slice type), [..-2])

Useful as it is backed by the original value, so the ownership rules apply
* Use the example in https://doc.rust-lang.org/book/ch04-03-slices.html 
  * Return a slice, instead of an index, for substring.


</details>
