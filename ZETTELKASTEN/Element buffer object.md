202511031801
Status: #idea
Tags: [[Graphics programming]]

# Element buffer object

> An *element buffer object* (*EBO, also sometimes called an **index buffer object, IBO***) is an [[OpenGL object]] that manages a part of the GPU's memory that stores indices. These indices refer to vertices in a *VBO*, and are used when drawing using `glDrawElements()` as opposed to `glDrawArrays()`.

The main use of *EBO*s is to eliminate repeated vertices in the vertex data, by defining each vertex only once, and describing their drawing order by index rather than the vertices themselves.
### Example for illustration
Imagine we want to draw a rectangle made up of two triangles. While `glDrawArrays()` would draw the vertices according to this array:
```c++
float vertices[] = {
    // first triangle
     0.5f,  0.5f, 0.0f,  // top right
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f,  0.5f, 0.0f,  // top left 
    // second triangle
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f, -0.5f, 0.0f,  // bottom left
    -0.5f,  0.5f, 0.0f   // top left
}; 
```
We can see two vertices here are repeated (top-left, bottom-right) and will take up extra space in the *VBO*.

Instead what we can do is define a vertices array with no duplicates (still stored in a *VBO* as  you normally would):
```c++
float vertices[] = {
     0.5f,  0.5f, 0.0f,  // top right
     0.5f, -0.5f, 0.0f,  // bottom right
    -0.5f, -0.5f, 0.0f,  // bottom left
    -0.5f,  0.5f, 0.0f   // top left 
};
```
and define an array of indices describing the order we want to pass over them to draw our shape (repetitions allowed, of course):
```c++
unsigned int indices[] = {  // note that we start from 0!
    0, 1, 3,   // first triangle
    1, 2, 3    // second triangle
};  
```

Then we can store this index data in an *EBO*, using the same kind of initialization we use for *VBOs*:
```c++
unsigned int EBO;
glGenBuffers(1, &EBO);

glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, sizeof(indices), indices, GL_STATIC_DRAW); 
```

All other initialization involving *VBO*s and *VAO*s is done as you normally would. 

Finally, during the main loop, instead of drawing using `glDrawArrays()`, we use `glDrawElements(mode, count, type, indices)`:
```c++
while(!glfwWindowShouldClose(window))
{
	...
	glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, EBO);
	glDrawElements(GL_TRIANGLES, 6, GL_UNSIGNED_INT, 0);
	...
}
```

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)