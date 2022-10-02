# Adding objects to the scene

Objects are easiest way to get started with the engine. They are essentially a struct that holds data enough to render something on the screen. You can learn more about them at [it's dedicated page](https://aryanpurtech.github.io/BlueEngineDocs/second_chapter/objects.html).

Primitive shapes in the engine define an Object for you. To add a shape to the engine, try importing a primitive shape, say, a square:

```rust
use blue_engine::primitive_shapes::square;
```

Then we can create a square by calling it:

```rust
square("my square", ObjectSettings::default(), &mut engine).unwrap();
```

The `"my square"` is the ID of your object. make sure to choose something that you can easily access later on. `ObjectSettings` is the settings for your object, they can essentially predefine some modifications for you. You can still modify later on as well.


