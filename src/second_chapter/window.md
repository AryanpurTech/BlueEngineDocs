# Windowing, input

Windowing in Blue Engine is handled by [winit](https://github.com/rust-windowing/winit), and the events are handled by [winit input helper](https://github.com/rukai/winit_input_helper). In the future SDL2 is an alternative planned implementation, but as of now winit handles all the windowing needs.

## Window settings

The window has a bunch of settings that can be changed and manipulated. These window settings are applied at the time of engine initialization. The settings exist as `WindowDescriptor` and the options and their default data are as such:

Parameter | Value
--------- | -----
width | 800
height | 600
title | "Blue Engine"
decorations | true
resizable | true

* Decorations are the title bar and the borders that windows have. Setting it to false will remove them, which is also called borderless windowing.

* Resizable is a setting that allows the windows to be resized or stay in a fixed size. Having this set to false will also disable maximize and minimize options.
