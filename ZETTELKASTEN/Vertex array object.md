202511031612
Status: #idea
Tags: [[Graphics programming]]

# Vertex array object

> A *vertex array object* (*VAO*) is a type of [[OpenGL object]] that stores a set of [[vertex attribute]] configurations. In other words, it carries information about what vertex attributes are enabled, which [[vertex buffer object]]s (*VBO*s) they read from, and in what format they're supposed to read from them.

To be more precise, a *VAO* stores:
- Calls to `glEnableVertexAttribArray` or `glDisableVertexAttribArray`.
- Vertex attribute configurations via `glVertexAttribPointer`.
- Vertex buffer objects associated with vertex attributes by calls to `glVertexAttribPointer`.

With this, we are able to switch between different vertex attribute configurations, that read from different *VBO*s, simply by binding different *VAO*s. See the below figure for an illustration of this.
![[vertex_array_objects.png]]
*Notice how each VAO has different attributes, that read from different VBOs, in a different format.*

### Setting up a VAO
Storing configuration data in a *VAO* is as simple as generating the *VAO* using `glGenVertexArrays()` and binding it using `glBindVertexArray()` before linking vertex attributes to *VBO*s using `glVertexAttribPointer()`

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)