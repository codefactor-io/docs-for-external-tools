Pattern: Overly complex type

Issue: -

## Description

Too complex types make the code less readable. Consider
using a `type` definition to simplify them.

## What it does

Checks for types used in structs, parameters and `let`
declarations above a certain complexity threshold.

## Examples

Example of **incorrect** code:

```rust
struct PointMatrixContainer {
    matrix: Rc<Vec<Vec<Box<(u32, u32, u32, u32)>>>>,
}

fn main() {
    let point_matrix: Vec<Vec<Box<(u32, u32, u32, u32)>>> = vec![
        vec![
            Box::new((1, 2, 3, 4)),
            Box::new((5, 6, 7, 8)),
        ],
        vec![
            Box::new((9, 10, 11, 12)),
        ],
    ];

    let shared_point_matrix: Rc<Vec<Vec<Box<(u32, u32, u32, u32)>>>> = Rc::new(point_matrix);

    let container = PointMatrixContainer {
        matrix: shared_point_matrix,
    };

    // ...
}
```

Example of **correct** code:

```rust
type PointMatrix = Vec<Vec<Box<(u32, u32, u32, u32)>>>;
type SharedPointMatrix = Rc<PointMatrix>;

struct PointMatrixContainer {
    matrix: SharedPointMatrix,
}

fn main() {
    let point_matrix: PointMatrix = vec![
        vec![
            Box::new((1, 2, 3, 4)),
            Box::new((5, 6, 7, 8)),
        ],
        vec![
            Box::new((9, 10, 11, 12)),
        ],
    ];

    let shared_point_matrix: SharedPointMatrix = Rc::new(point_matrix);

    let container = PointMatrixContainer {
        matrix: shared_point_matrix,
    };

    // ...
}
```

## Further Reading

* [Clippy - type_complexity](https://clippy.rust-lang.org/stable/index.html#type_complexity)
