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
