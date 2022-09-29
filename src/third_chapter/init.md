# Window creation

For setup, check `setup` page from first chapter. To create a window in Blue Engine, first initialize the engine:

```rust
let mut engine = Engine::new(WindowDescriptor::default()).expect("Couldn't init the Engine"); 
```

This will initalize the engine, and making components ready for use. The engine by itself can't do anything, you'll need to start the update loop for things to happen:

```rust
engine.update_loop(move |_, _, _, _, _| {}).expect("Error during update loop");
```

The `update_loop` function takes in a closure, that it'll be run every frame. Try running it and you should see a blank window:

```bash
cargo run
```

