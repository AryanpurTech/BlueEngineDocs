# Engine introduction

`Engine` is the starting point for using the BE (Blue Engine). It acts like a tree, with each branch being a functionality. This is an opinionated approach and not often liked by all of Rust's community as it brings up some issues for the borrow checker. However it is much more mature than early testings and it appears to be working for our case, so unless highly requested or a major issue appears it will remain in such way.

The `Engine` is a `struct` type, and contains:

* `Renderer`
* `Window`
* `Objects`
* `Camera`
* `event_loop` [hidden to create only]

We will discuss each of them in great detail later on. For now, let's look at an example on how to start using the `Engine`.

```rust
// import the Engine and WindowDescriptor from the header.
use blue_engine::header::{Engine, WindowDescriptor};

fn main() {
    // you can create the engine through the Engine::new()
    // it returns a Result<Engine>
    let engine = Engine::new(WindowDescriptor::default()).expect("Couldn't create the engine");
}
```

`WindowDescriptor` is used for window settings as the `Engine` initializes it too. The `WindowDescriptor` has these default values:

Parameter | value
--------- | -----
width | 800
height | 600
title | Blue Engine
decorations | true
resizable | true

You can also alter only few and leave the rest as default.
