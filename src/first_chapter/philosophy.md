# Philosophy, structure, and technologies

## Philosophy

The philosophy is always to bring as much ease of use and flexibility as possible. Anything done with the engine, the changes made, the features added, e.t.c. are all made to be as easy-to-use and as flexible as possible for everyone to have a peace of mind when using. Doing graphics shouldn't be hard even at such low level right?

For most people, use cases differ. And because of that, the level of abstraction should differ too; the engine must be flexible enough to accommodate that. This is how Blue Engine can be as high or low level when using as you need. Just need objects to be displayed? Sure thing, they're just one line away! Want to have custom built structure for your own shape and bring your custom engines upon it with custom shaders, textures, and more? We got you covered too! There's something for everyone!

## Structure

To achieve this goal, the Blue Engine source code is structured in a flexible way. All definitions, such as `structs`, `types`, and `enums`, are defined in a single header file, `header.rs`. This file also specifies whether each part will be public for external use or not, as well as defining global default settings, such as default textures and shaders.

The methods' code is organized under their respective files, with the target classes taken from the definitions file. For example, methods related to rendering live under a `render.rs` file, while camera functionality lives in a separate `camera.rs` file. This structure allows for clean progress and minimizes interference between different parts of the engine.

## Technologies used

The Blue Engine uses a combination of standard Rust library functions and external crates to achieve its goals. While we prioritize using the standard library as much as possible, there are some tasks that require more advanced functionality or are not feasible within its bounds. For these cases, we turn to external crates.

The current list of dependencies for Blue Engine can be found in the `cargo.toml` file located in the root directory.

## Dependency justification as of 0.5.1

* `futures = "0.3"`: This dependency is used to enable blocking within async functions that are utilized in lower-level APIs.

* `winit = { version = "0.29.8", features = ["rwh_05"] }`: This crate handles the creation and control of windows and contexts, ensuring a consistent interface across various platforms.

* `image = "0.24"`: The image crate is used for reading and handling textures within the engine.

* `bytemuck = { version = "1.14", features = ["derive"] }`: This dependency provides utility functions for casting between plain data types, which is necessary for sending data to the GPU.

* `winit_input_helper = "0.15"`: This crate simplifies the process of gathering input event data and provides an easy-to-use list of functions for accessing them.

* `anyhow = "1.0"`: This dependency is used for error handling, providing a clear and concise way to handle errors within the engine.

* `downcast = "0.11`: This dependency helps with downcasting trait objects of plugins into usable components.

* `wgpu = { version = "0.18" }`: The wgpu crate acts as a wrapper over the graphics API and follows the WebGPU standard. It provides an intuitive and performant way to render graphics across multiple platforms.

* `nalgebra-glm = "0.18"`: This math library is used extensively throughout the engine for handling various mathematical operations.

## Optional dependencies

* `android_logger = { version = "0.13", optional = true }` : This dependency is used for logging on Android.

* `log = { version = "0.4", optional = true }`: same use as `env_logger`

* `env_logger = { version = "0.10", optional = true }`: This logging library is used internally for event logging, as well as for providing useful debugging information.
