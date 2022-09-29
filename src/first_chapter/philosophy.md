# Philosophy, structure, and technologies

## Philosophy

The philosophy is always to bring as much ease of use and flexibility as possible. Anything done with the engine, the changes made, the features added, e.t.c. are all made to be as easy-to-use and as flexible as possible for everyone to have a peace of mind when using. Doing graphics shouldn't be hard even at such low level right?

For most people, use cases differ. And because of that, the level of abstraction should differ too; the engine must be flexible enough to accommodate that. This is how Blue Engine can be as high or low level when using as you need. Just need objects to be displayed? Sure thing, they're just one line away! Want to have custom built structure for your own shape and bring your custom engines upon it with custom shaders, textures, and more? We got you covered too! There's something for everyone!

## Structure

The source code is structured to have a common place for every part of the engine. I took a bit of idea from structures of C/C++ projects for organizing the source code. And came up with a similar organizational structure.

* all the `structs`, `types`, `enums`, e.t.c. are all under `header.rs` file. This file also specify if a part will be public for other crate use or not as well as global default data, such as default texture, default shader, and more.

* Methods' code and implementation live under their designated file. The target classes will be taken from the definitions file.

* Methods' code and other parts like camera, window, render, e.t.c. will each have their own files for custom and clean progress and to not interfere with each-other.

## Technologies used

I try to use standard library as much as possible, but some parts are too much to write, or not possible within the bounds of standard library such as windowing, rendering APIs, e.t.c. For these, I use crates that already provide those. Even if a need for an external crate rises, I try as much as possible to ensure cross-platform portability, ease of use, and keep it as lightweight as possible, and to not be a roadblock for development and use.

The technologies used as of now, can be viewed on the `cargo.toml` file in the root directory under `dependencies` section.

## Dependency justification as of 0.3.7

* `futures = "0.3.21"`: is used for blocking the async functions that is used internally in lower level apis.

* `winit = "0.26.1"`: handles the creation and control of windows and contexts.

* `image = "0.24.2"`: used for texture reading and handling of images.

* `bytemuck = { version = "1.10.0", features = ["derive"] }`: small utilities for casting between plain data types. Helps with sending bytes to gpu.

* `winit_input_helper = "0.12.0"`: helps with gathering input event data, and leaving an easy-to-use list of functions to access them. It's more of a quality-of-life dependency.

* `anyhow = "1.0.57"`: helps with error handling.

* `env_logger = "0.9.0"`: Logs internal events, and gives useful error and logs. Very good for debugging!

* `wgpu = { version = "0.13.0" }`: a wrapper over graphics api, based on WebGPU standard. Very awesome api for rendering graphics that just makes sense! It also helps with having your graphic run everywhere optimally.

* `nalgebra-glm = "0.17.0"`: math library for all the math that is used in the engine.

---

These are optional dependencies that are enabled with flags:

* `gltf = { version = "1.0.0", optional = true }`: used for handling gltf 2.0 and glb files. Enabled with `model_loader` feature flag.

* `imgui-wgpu = { version = "0.20.0", optional = true }`, `imgui-winit-support = { version = "0.8.2", optional = true, features = [ "winit-26", ] }`, and `imgui = { version = "0.8.2", optional = true }`: are used for GUI (Graphical User Interface), uses industry-proven c++ imgui library. This can be enabled with `gui` feature flag.
