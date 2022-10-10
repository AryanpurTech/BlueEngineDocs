# Hello World

## Setting up

Firstly let's create a new rust project:

```bash
cargo init --bin blue_graphics
```

After that's taken care of, open `cargo.toml` and add the crate under dependencies:

```toml
[dependencies]
blue_engine = "*"
```

This should now install Blue Engine and all it's dependencies. We should be ready to get started.

## Engine initialization

Alright, now that we're done with that, let's get the exciting work started! Firstly, we will create a new window so that later we can draw under it!

Firstly, open the `main.rs` file under `src` folder, and paste below in it:

```rust
use blue_engine::header::{Engine, WindowDescriptor};         // 0

fn main(){
  let mut engine = Engine::new(WindowDescriptor::default())  // 1
    .expect("Couldn't init the Engine");                     // 2

    engine
        .update_loop(move |_, _, _, _, _| {})                 // 3, 4
        .expect("Error during update loop");                 // 5
}
```

0. We need some structs to initialize the engine.
1. We initialize the Engine and start to describe how the window should look like. For now, we'll use the default values.
2. The initialization returns a `Result<Engine>` which you can unwrap. This way you can also check if there is any error during the creation of the Engine.
3. The update loop is responsible for everything that you will do that needs to be updated or checked every frame. This includes checking for events such as inputs, or updating certain things if a change happens.
4. The _ are to not use the parameters passed on. The update loop gives you access to 5 things in this order:
   1. renderer
   2. window
   3. objects
   4. events
   5. camera
5. Update loop also returns a `Result<()>`. The errors that will happen through this means something during the update loop. So make sure to check for errors during the update loop as well, or not if you're a brave soul :)

After you're done, you can run:

```bash
cargo run
```

You should now see an empty window! Congratulations you just created your first window using Blue Engine!
