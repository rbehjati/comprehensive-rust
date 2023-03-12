# Traits

Rust lets you abstract over types with traits. They're similar to interfaces:

```rust,editable
trait Shape {
    fn draw(&self);
}

struct Circle {
    center: Point,
    radius: i32,
}

struct Polygon {
    points: Vec<Point>,
}

struct Point {
    x: i32,
    y: i32,
}

impl Point {
    fn new(x: i32, y: i32) -> Point {
        Point { x, y }
    }
}

impl Shape for Circle {
    fn draw(&self) {
        println!("Circle centered at ({}, {}) with radius {}!", self.center.x, self.center.y, self.radius);
    }
}

impl Shape for Polygon {
    fn draw(&self) {
        println!("Polygon with {} points!", self.points.len());
    }
}

fn main() {
    let points = vec![Point::new(0, 0), Point::new(1, 1), Point::new(0, 1)];
    let shapes: Vec<Box<dyn Shape>> = vec![
        Box::new(Circle { center: Point::new(0, 0), radius: 5 }),
        Box::new(Polygon { points }),
    ];
    for shape in shapes {
        shape.draw();
    }
}
```

<details>

* Traits may specify pre-implemented (default) methods and methods that users are required to implement themselves. Methods with default implementations can rely on required methods.
* Types that implement a given trait may be of different sizes. This makes it impossible to have things like `Vec<Shape>` in the example above. Try replacing shapes with the following.

```
        let shapes = vec![
            Circle { center: Point::new(0, 0), radius: 5 }, 
            Polygon { points }
        ];
```

* `dyn Shape` is a way to tell the compiler about a dynamically sized type that implements `Shape`. These are called trait objects.

* In the example, `shapes` holds Fat Pointers to objects that implement `Shape`. The Fat Pointer consists of two components, a pointer to the actual object and a pointer to the virtual method table for the `Shape` implementation of that particular object.

Compare these outputs in the above example:
```rust,ignore
    println!("{} {}", std::mem::size_of::<Circle>(), std::mem::size_of::<Circle>());
    println!("{} {}", std::mem::size_of::<&Polygon>(), std::mem::size_of::<&Polygon>());
    println!("{}", std::mem::size_of::<&dyn Shape>());
    println!("{}", std::mem::size_of::<Box<dyn Shape>>());
```

</details>
