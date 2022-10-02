# Window creation and Customization

## Window creation

For setup, check [setup](https://aryanpurtech.github.io/BlueEngineDocs/first_chapter/setup.html) page from first chapter. To create a window in Blue Engine, first initialize the engine:

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

This means everything is working. We will draw things in it later on, for now let's try changing the window a bit.

The default window has a small size, and a default title. Let's say we want to change it from `800x600` to `1280x720` and change title to `My Awesome Render`. There are two ways to accomplish this.

## Customize at start with `WindowDescriptor`

At the start, we declared a default `WindowDescriptor`, we can define our desired customization there to reflect it globally. To do this, simple define the `width`, `height`, and `title` fields in the `WindowDescriptor`:

```rust
WindowDescriptor {
    width: 1280,
    height: 720,
    title: "My Awesome Render",
    ..Default::default() // To keep other details to default values
}
```

## Customize later on the runtime

During runtime, these options are available too! These settings can be accessed through `window` property of the `Engine` struct. Before `update_loop` simple use `engine.window.`, or during `update_loop` the window is exposed to the loop directly, and then type the setting you want, e.g. `set_inner_size` method for size. For our case, we can do this:

```rust
engine.window.set_inner_size(PhysicalSize::new(1280, 720));
engine.window.set_title("My Awesome Render");
```

Notice that we use `set_` before every option method, and we use `PhysicalSize` for size. There is also `LogicalSize` which you can use.
