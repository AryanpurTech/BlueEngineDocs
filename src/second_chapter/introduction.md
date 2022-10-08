# Engine introduction

## Engine

`Engine` is the starting point for using the BE (Blue Engine). It acts like a tree, with each branch being a functionality. This is an opinionated approach and not often liked by all of Rust's community as it brings up some issues for the borrow checker. However  it appears to be working for our case, so unless highly requested or a major issue appears it will remain in such way. In future the monolithic structure will be changed with modular approach, but as of current versions, it will remain as such.

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

After you initialized the engine, you can start the update loop. The update loop runs code per frame, and also provides events and updates.

> note that the events are updated BEFORE each frame! So any changes you make in this frame, will be updated on the next frame.

## Update loop

The update loop is method of `Engine` that has one parameter which is a mutable callback function, that are grouped into two section and provides these:

### Core

* `&mut Renderer`
* `&mut Window`
* `&mut Vec<Object>`

### Utils

* `&Input`
* `&mut Camera`
* `(&mut CommandEncoder, &TextureView)`
* `&mut Vec<T>` where `T: UpdateEvents + 'static`
  
The fields that are not mutable are only there to provide information. The mutable fields are the ones where your changes will exist, such as showing things on screen, moving camera, e.t.c.

Once you run the update_loop, the window will start to appear. You can also leave the loop empty for an empty screen! The loop also allows to use the `move` keyword before for passing variables from outside the scope to the inside of the loop.

Creating an update loop that's empty is as easy as:

```rust
// the underscores shows that we do not want to use them now.
// The `move` keyword makes it possible to use variables from outside of the loop scope.
engine.update_loop(move |_, _, _, _, _| {})
        .expect("Error during update loop");
```

This function returns a `Result<()>`.
