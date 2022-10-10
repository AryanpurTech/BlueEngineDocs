# Setup

To start, we need to setup the framework first. This guide expects you to know basics of Rust. If not, start [here](https://rust-lang.org)

Fortunately, the installation is very simple; thanks to rust's ecosystem. Because we're using Rust, make sure you have it [installed](https://www.rust-lang.org/tools/install) and working properly along `cargo`.

## Examples

If you'd like to try testing the engine before starting to work with it, you'd need to download/clone the repository.

```bash
git clone https://github.com/AryanpurTech/BlueEngine

cd BlueEngine 
```

After that, you can try running examples that are currently provided. For example, let's try running Triangle example that shows a white-ish triangle on your screen:

```bash
cargo run --example triangle
```

Cargo will download dependencies, setup the engine, and run the example. After it's all done, a window will appear with the triangle in middle. If you can't see a triangle, make sure that your drivers are up-to-date. If any errors were shown on console and you think might be source of the problem, feel free to [open a new issue](https://github.com/AryanpurTech/BlueEngine/issues) and I'll look into it.

The [examples](https://github.com/AryanpurTech/BlueEngine/tree/master/examples) folder provides valuable source of examples on how the engine can be used. More examples will be added as the time goes. Although the API is unstable now, the examples keep up with the latest API changes.

## New Blue Engine project

To start a new Blue Engine project, open your command line in the desired folder, and create a new project with cargo:

```bash
cargo init my_awesome_be_project
```

Make sure to replace `my_awesome_be_project` with your desired name, or, just leave it with that, we know it'll be awesome either way :D

After that, add this as dependency in your `Cargo.toml` in the project folder:

```toml
# The star tells the package manager to download the latest version
blue_engine = "*"
```

If you want a specific version, you can specify it too! E.g. the current published version as of this writing:

```toml
blue_engine = "0.3.7"
```

If you'd like to enable an optional feature, you can specify it in the `features` list:

```toml
# For example enable gui support
blue_engine = { version = "*", features = ["model_loading"] }
```

That's it! Just open the `main.rs` file in the `src` folder and make the world a better place!

## Turbo build times

This will allow fast build times on debug. This works by building a shared library/dynamic library and linking it with executable. Rust's compiler spends quite some time to pack and link everything into an exectuable on each build, so this will remove the need to repack and link the engine, thus improving the build times significantly. There are a few steps to follow, but they're not hard.

> `DO NOT USE FOR FINAL RELEASE! OR ELSE WILL NEED TO COPY EXTRA FILES ALONG YOUR EXECUTABLE.`

### Clone the engine

We first start by cloning the engine from github. Move to parent directory of your project, and clone the engine:

```bash
git clone https://github.com/AryanpurTech/BlueEngine
```

Your project structure should look something like this:

```bash
Projects:
    - blue_engine
    - my_app
```

With `my_app` being your project. This way it ensures you can use it for multiple projects at once too as it's a one-time setup.

### Setup the engine

Open the engine's folder, and add this to the `Cargo.toml` under `[lib]`.

```toml
crate-type = ["dylib"]
```

This essentially tells the compiler to compile the engine as a shared library/dynamic library, after finishing the setup, in the build folder you should be able to see a file with similar name to `libblue_engine`.

### Setup your project

And on your project's `Cargo.toml` under `[dependencies]`, add `path = "../blue_engine"` to the `blue_engine` as such:

```toml
blue_engine = { path = "../blue_engine", .. } # replace the .. with the rest. e.g. version, features, e.t.c.
```

#### Windows

For windows, you need to go one more step. This essentially doesn't work normally, hence you'll need to add some more configuration and switch to nightly.

Switch to nightly:

```bash
rustup override set nightly
```

This sets current project to nightly only. And next step is in your project's directory, add a folder with the name `.cargo`, and add a file in it with the name `config.toml` and copy these into it:

```toml
[target.x86_64-pc-windows-msvc]
linker = "rust-lld.exe"
rustflags = ["-Zshare-generics=off"]
```

### Enjoy fast builds

And that's it! You should now see faster build times. For final release versions, make sure to just remove `path = "../blue_engine"` from dependency, and you should be good to go for release. You can also configure it in `Cargo.toml` to use the path for debug profile and non turbo build for release profile as well.
