# immutable variables, mutable variables and constants

## immutable variables
cannot assign new value.
```rust
let num = 1;
num = 2; // COMPILATION ERROR!
```

can create a new variable of same name with `let`, or a constant of same name with `const`. the previous variable 
no longer works. this is called [shadowing](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html#shadowing).
```rust
let num = 1;
let num = 2; // ok
let mut num = 3; // ok
const num: u32 = 4; // ok
```

## mutable variables
can assign new value but type must match.
```rust
let mut num = 1;
num = 2; // ok
num = "three"; // COMPILATION ERROR! MISMATCHED TYPE
```

if you use `let` then you're creating a new variable (mut or not) so 
the type can be different:
```rust
let mut num = 1;
let num = "two"; // ok
let mut num = 3.4; // ok
```

## constants
obviously you can't change a constant's value
```rust
const HOUR_IN_MINUTES: u32 = 60; 
HOUR_IN_MINUTES: u32 = 80; // COMPILATION ERROR!
```

must annotate the type.
```rust
const HOUR_IN_MINUTES = 60; // COMPILATION ERROR! MUST ANNOTATE TYPE!
const HOUR_IN_MINUTES: u32 = 60; // ok
```

shadowing works here as well. 
```rust
const HOUR_IN_MINUTES: u32 = 60; 
let HOUR_IN_MINUTES = 70; 
const HOUR_IN_MINUTES: u16 = 80;
```

The compiler is able to evaluate a limited set of operations at compile time, which lets us choose to write out this value in a way that’s easier to understand and verify, rather than setting this constant to the value 10,800. See the [Rust Reference’s section on constant evaluation](https://doc.rust-lang.org/reference/const_eval.html) for more information on what operations can be used when declaring constants.
```rust
const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3; // ok
```
