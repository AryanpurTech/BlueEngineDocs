# Renderer

Let's talk about the renderer. `Renderer` handles everything that is about talking with the GPU to render things you specify. This includes

* Shaders
* Textures
* Vertices
* Uniform Buffers
  
We'll discuss more about each of them later on, for now let's talk about how it looks like and how it works.

BE provides many verity on creation of them. You can build, append, or build and append. you can also update and remove them!

There are default data of them except for vertices. The exist on the 0th index. Which includes a default uniform buffer (transformation, camera and color), a default texture (one white pixel), and a default shader. We'll talk about them later on.

## Pipeline

The Pipeline is the way that BE handles data to renderer. BE stores data for rendering on a dynamically sized array and gives you their index on time of creation. A `Pipeline` struct holds one index for each of those four things listed above. At time of render, the values are then fetched from the array and sent to GPU. We will learn about the order and position of each of them when rendering, later. For now, think of pipeline as the data holder of your object.

## Shader

Shaders are programs that run in the GPU. BE uses [WGSL](https://www.w3.org/TR/WGSL/) which is the main shading language of WebGPU.

As of yet, only vertex and fragment stages are supported. You can also change many other aspects such as cull face, render mode, and more at the time of shader creation!

You can change those settings through the `ShaderSetting`, and of course default settings also exist. They are:

Parameter | Value
--------- | -----
topology | TriangleList
strip_index_format | None
front_face | Ccw
cull_mode | Back
polygon_mode | Fill
clamp_depth | false
conservative | false
count | 1
mask | !0
alpha_to_coverage_enabled | false

To create a new shader through BE and append it to the storage for render, you can use the `build_and_append_shader()`.

> The shader source as of yet (0.2.5) only supports WGSL, but later on the support for SPIR-V compiled shaders will also be available.

## Textures

Textures are images that can be burned to vertices on the scene. They have all sorts of uses, e.g. adding textures to plane to make it look like a wall or ground, or textures to character shapes for more details.

As of now (0.2.5), BE only supports RGBA based textures. PNG is the recommended file format and the format is Rgba8UnormSrgb.

There's two ways to create BE textures

1. Creating an `image::DynamicImage` and appending that
2. Using bytes of the image and creating one.

`image` is a rust crate that BE uses under the hood for processing texture data.

BE also allows for different modes of the texture in case the texture couldn't fit, which are:

* Clamp
* Repeat
* Mirror repeat

The textures are sampled as well, and they can be accessed on group 0 on slot:

0. Texture
1. Sampler

## Vertices

Vertices
