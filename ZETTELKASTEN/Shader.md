202511011252
Status: #idea
Tags: [[Graphics programming]]

# Shader

> *Shaders* are small specialized programs that run on the many small cores of the GPU, each with the purpose of completing one of the steps of the graphics pipeline of OpenGL.

 So for instance a *vertex shader* is a program whose purpose is to take in *vertex data* (array of coordinates) as input, and convert these coordinates to points in space, which is the first step of the graphics pipeline. Another example is the a *fragment shader*, whose job is to take in a rasterized set of pixels (e.g. a triangle primitive converted from a purely mathematical shape into a set of pixels) and add color to them, which is another step of the graphics pipeline.

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)