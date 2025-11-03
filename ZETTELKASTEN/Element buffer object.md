202511031801
Status: #idea
Tags: [[Graphics programming]]

# Element buffer object

> An *element buffer object* (*EBO, also sometimes called an **index buffer object, IBO***) is an [[OpenGL object]] that manages a part of the GPU's memory that stores indices. These indices refer to vertices in a *VBO*, and are used when drawing using `glDrawElements()` as opposed to `glDrawArrays()`.

The main use of *EBO*s is to eliminate repeated vertices in the vertex data, by defining each vertex only once, and describing their drawing order by index rather than the vertices th

___
# References
