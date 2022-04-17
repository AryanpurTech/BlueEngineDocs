# Camera

Camera in Blue Engine is default initialized upon creation. This may change in the future, but as of yet a default camera is created. This camera is left-hand perspective camera, and some default values are assigned according to the window which are as such:

Parameter | Value
--------- | -----
position | (0f32, 0f32, 1f32)
target | (0f32, 0f32, 0f32)
up | (0f32, 1f32, 0f32)
aspect | window_width / window_height
fov | 70f32 * (PI / 180f32)
near | 0.1f32
far | 100f32
view_data | DEFAULT_MATRIX_4

* position, target, and up defines how the camera views the scene, changing these parameters allow you to alter the view.
* fov is in radians instead of degrees.
* near and far define how close and how far can the camera sees, changing these values will alter how much further or near are things in your scene visible.
* view data is a matrix containing the matrix that will be applied to the scene during render, you usually don't have to deal with this directly.

Along with these options, you can alter the parameters through methods that are assigned. For example `set_position` to change the position of the camera in the scene. Each of these methods start with `set_` and then the option name, e.g. `set_fov` or `set_far`.

More options and features will be added as time goes.
