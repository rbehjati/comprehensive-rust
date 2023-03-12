# Trait Objects

How can we store a collection of mixed types that implement `Shape`?

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

Memory layout after allocating `shapes`:

```bob
 Stack                             Heap
.- - - - - - - - - - - - - -.     .- - - - - - - - - - - - - - - - - - - - - - - -.
:                           :     :                                               :
:    shapes                 :     :                                               :
:   +-----------+-------+   :     :   +-----+-----+                               :
:   | ptr       |   o---+---+-----+-->| o o | o o |                               :
:   | len       |     2 |   :     :   +-|-|-+-|-|-+                               :
:   | capacity  |     2 |   :     :     | |   | |   +------------------------+    :
:   +-----------+-------+   :     :     | |   | '-->| ptr, len, capacity,... |    :
:                           :     :     | |   |     +------------------------+    :
`- - - - - - - - - - - - - -'     :     | |   |                                   :
                                  :     | |   |    +----------------------------+ :
                                  :     | |   '--->| "<Polygon as Shape>::draw" | :
                                  :     | |        +----------------------------+ :
                                  :     | |                                       :
                                  :     | |   +-----------------+                 :
                                  :     | '-->| center, radius  |                 :
                                  :     |     +-----------------+                 :
                                  :     |                                         :
                                  :     |     +---------------------------+       :
                                  :     '---->| "<Circle as Shape>::draw" |       :
                                  :           +---------------------------+       :
                                  :                                               :
                                  :                                               :
                                  '- - - - - - - - - - - - - - - - - - - - - - - -'
```

