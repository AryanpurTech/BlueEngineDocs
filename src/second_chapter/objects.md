# What are objects?

An object in Blue Engine is a collection of a vertex buffer, shader, texture, and maybe a uniform buffer, and allows various operations on them such as scaling, translation, change in data, and more. Objects are similar to nodes in Godot. Other traits can be applied to them to add extra functionalities that are desired. Objects are the only things are are sent for render and they are the very basic element of Blue Engine. Unlike the many structures that exist so far, objects do not have a parent or a child, and does not work in a tree structure. Instead the objects are stored in a dynamically sized array which then are iterated upon when rendering.

## Initialization

A new object can be created by using the engine's `new_object` method. Three arguments are required:

* Vertices: a `Vec<Vertex>` which includes the vertices for your object.
* Indices: a `Vec<u16>` which includes the indices of your vertices.
* `ObjectSettings` which is a struct defining the structure and settings for the object. These can later on be changed as well. The list of options along their default values are as such:

Parameter | Value
--------- | -----
name | Some("Object!")
size | (100f32, 100f32, 100f32)
scale | (1f32, 1f32, 1f32)
position | (0f32, 0f32, 0f32)
color: | uniform_type::Array [DEFAULT_COLOR]
camera_effect | true
shader_settings | ShaderSettings::default()

* color's uniform type of array is due to the color being passed down to the uniform buffer and applied at fragment stage.
* camera effect defines if the camera transformations have any effect on the object. An object with camera effect as false will not experience any move from camera unless manually moved, and also will not be affected by POV change or anything else related to cameras.
* shader settings are a collection of settings related to the shaders, their options and default values are defined in the renderer page of this guide.
  
Upon creation, an `&mut Object` will be returned wrapped in `Result`. Which then you can further change and update.
