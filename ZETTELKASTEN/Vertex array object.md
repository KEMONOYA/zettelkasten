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
Storing configuration data in a *VAO* is as simple as generating the *VAO* using `glGenVertexArrays()` and binding it using `glBindVertexArray()` **before** linking vertex attributes to *VBO*s using `glVertexAttribPointer()` and `glEnableVertexAttribArray()`, then unbinding the *VAO* in the end. By configuring the vertex attributes while a *VAO* is bound, these configurations are stored in the *VAO*.

Example:
```c++
GLuint VAO, VBO;
glGenVertexArrays(1, &VAO);
glGenBuffers(1, &VBO);

glBindVertexArray(VAO);

glBindBuffer(GL_ARRAY_BUFFER, VBO);
glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);

glBindBuffer(GL_ARRAY_BUFFER, 0); // VBO got linked to attribute index 0 above, so we don't need this VBO to be bound anymore, VAO stored its linking
glBindVertexArray(0);
```

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)