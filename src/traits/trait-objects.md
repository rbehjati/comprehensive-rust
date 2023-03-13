# Trait Objects


A trait object (specified using [dyn](https://doc.rust-lang.org/std/keyword.dyn.html)) points to
both an instance of a type implementing our specified trait and a table used to look up trait
methods on that type at runtime.

```rust
trait Greet {
    fn say_hello(&self);
}

struct Dog {
    name: String,
}

struct Cat;  // No name, cats won't respond to it anyway.

impl Greet for Dog {
    fn say_hello(&self) {
        println!("Wuf, my name is {}!", self.name);
    }
}

impl Greet for Cat {
    fn say_hello(&self) {
        println!("Miau!");
    }
}

fn main() {
    let pets: Vec<Box<dyn Greet>> = vec![
        Box::new(Dog { name: String::from("Fido") }),
        Box::new(Cat),
    ];
    for pet in pets {
        pet.say_hello();
    }
}
```


Memory layout after allocating `pets`:

```bob
 Stack                             Heap
.- - - - - - - - - - - - - -.     .- - - - - - - - - - - - - - - - - - - - - - - - - -.
:                           :     :                                                   :
:    xs                     :     :                                                   :
:   +-----------+-------+   :     :   +-----+-----+                                   :
:   | ptr       |   o---+---+-----+-->| o o | o o |                                   :
:   | len       |     2 |   :     :   +-|-|-+-|-|-+                                   :
:   | capacity  |     2 |   :     :     |     | |   +----+----+---+----+              :
:   +-----------+-------+   :     :     |     | '-->| F  | i  | d | o  |              :
:                           :     :     |     |     +----+----+---+----+              :
`- - - - - - - - - - - - - -'     :     |     |                                       :
                                  '- - - - - - - - - - - - - - - - - - - - - - - - - -'
                                        |     |     +-----------------------------+    
                                        |     '---->| "<Dog as Greet>::say_hello" |    
                                        |           +-----------------------------+    
                                        |                                              
                                        |                                              
                                        |                                              
                                        |                                              
                                        |                                              
                                        |     +-----------------------------+          
                                        '---->| "<Cat as Greet>::say_hello" |          
                                              +-----------------------------+         
                                  

```

<details>

* You did not get into that issue in your `Shapes` excercise in Day-2 because you used an enum.

* Trait objects aren’t as generally useful as objects in other languages: their specific purpose is to allow abstraction across common behavior.

* [Object Safety](https://doc.rust-lang.org/reference/items/traits.html#object-safety): Not every Trait can be made into a Trait Object. 

* With trait objects, you get dynamic dispatch. This is as opposed to monomorphization that provides static dispatch.
  * Static dispatch: the compiler knows what method you’re calling at compile time.
  * Dynamic dispatch: the compiler can’t tell at compile time which method you’re calling, but emits code that at runtime will figure out which method to call.

</details>