# Setup

To start, we need to setup the framework first. This guide expects you to know basics of Rust. If not, start [here](https://rust-lang.org)

Fortunately, the installation is very simple; thanks to rust's ecosystem. Because we're using Rust, make sure you have it [installed](https://www.rust-lang.org/tools/install) and working properly along `cargo`.

## Examples

If you'd like to try testing the engine before starting to work with it, you'd need to download/clone the repository.

```bash
git clone https://github.com/ElhamAryanpur/BlueEngine

cd BlueEngine 
```

After that, you can try running examples that are currently provided. For example, let's try running Triangle example that shows a white-ish triangle on your screen:

```bash
cargo run --example triangle
```

Cargo will download dependencies, setup the engine, and run the example. After it's all done, a window will appear with the triangle in middle. If you can't see a triangle, make sure that your drivers are up-to-date. If any errors were shown on console and you think might be source of the problem, feel free to [open a new issue](https://github.com/ElhamAryanpur/BlueEngine/issues) and I'll look into it.

The [examples](https://github.com/ElhamAryanpur/BlueEngine/tree/master/examples) folder provides valuable source of examples on how the engine can be used. More examples will be added as the time goes. Although the API is unstable now, the examples keep up with the latest API changes.
