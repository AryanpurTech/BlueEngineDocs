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
