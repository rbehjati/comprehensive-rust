# Stack Memory

Creating a `String` puts fixed-sized data on the stack and dynamically sized
data on the heap:

```rust,editable
fn main() {
    let s1 = String::from("Hello");
}
```

```bob
 Stack                             Heap
.- - - - - - - - - - - - - -.     .- - - - - - - - - - - - - - - -.
:                           :     :                               :
:    s1                     :     :                               :
:   +-----------+-------+   :     :   +----+----+----+----+----+  :
:   | ptr       |   o---+---+-----+-->| H  | e  | l  | l  | o  |  :
:   | len       |     5 |   :     :   +----+----+----+----+----+  :
:   | capacity  |     5 |   :     :                               :
:   +-----------+-------+   :     :                               :
:                           :     `- - - - - - - - - - - - - - - -'
`- - - - - - - - - - - - - -'
```

<details>

Try:
* `println!("size: {}, len: {}, cap: {}", std::mem::size_of_val(&s1), s1.len(), s1.capacity())`

* then `println!("{}", std::mem::size_of::<usize>());`
</details>
