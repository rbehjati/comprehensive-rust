# Scalar Types

|                        | Types                                      | Literals                      |
|------------------------|--------------------------------------------|-------------------------------|
| Signed integers        | `i8`, `i16`, `i32`, `i64`, `i128`, `isize` | `-10`, `0`, `1_000`, `123i64` |
| Unsigned integers      | `u8`, `u16`, `u32`, `u64`, `u128`, `usize` | `0`, `123`, `10u16`           |
| Floating point numbers | `f32`, `f64`                               | `3.14`, `-10.0e20`, `2f32`    |
| Strings                | `&str`                                     | `"foo"`, `r#"\\"#`            |
| Unicode scalar values  | `char`                                     | `'a'`, `'α'`, `'∞'`           |
| Byte strings           | `&[u8]`                                    | `b"abc"`, `br#" " "#`         |
| Booleans               | `bool`                                     | `true`, `false`               |

The types have widths as follows:

* `iN`, `uN`, and `fN` are _N_ bits wide,
* `isize` and `usize` are the width of a pointer,
* `char` is 32 bit wide,
* `bool` is 8 bit wide.

<details>

 * The size of isize & usize is determined by the processor architecture

 * The type of unsuffixed numeric literals (e.g., not ending with i32 or _f32) will depend on how they are used. If no constraint exists, the compiler will use i32 for integers, and f64 for floating-point numbers.


  * Raw strings and raw byte strings: they don’t process any scapes [[ref]](https://web.mit.edu/rust-lang_v1.25/arch/amd64_ubuntu1404/share/doc/rust/html/reference/tokens.html#raw-string-literals)
    * Useful for specifying regular expressions.
  * b"abc" is the same as "abc".as_bytes()
  
**char**

* Since ‘character’ isn’t a well-defined concept in Unicode, char is a ‘Unicode scalar value’, which is similar to, but not the same as, a ‘Unicode code point’.
* 32 bits (4 bytes) fixed size
  * UTF-8 encodes code points in one to four bytes, depending on the value of the code point.
* char is always four bytes in size. This is a different representation than a given character would have as part of a String. 

</details>
