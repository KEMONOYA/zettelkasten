202511031131
Status: #idea
Tags: [[Graphics programming]]

# Vertex buffer object

> A *vertex buffer object* (*VBO*) is a type of [[OpenGL object]] that represents a region of the GPU's memory which holds [[vertex]] data. Storing vertex data in a *VBO* allows the GPU (e.g. the [[vertex shader]]) to access this data quickly and efficiently, instead of waiting for it to be sent from the CPU, which takes a considerable amount of time.

When we want to use the data inside a *VBO* as inputs to the [[vertex shader]], we bind it to the `GL_ARRAY_BUFFER` target using `glBindBuffer(GL_ARRAY_BUFFER, vbo1_ID)`. Inside OpenGL's internal state, it has a state variable storing "which buffer object is currently bound for the `GL_ARRAY_BUFFER` target," and it is this currently bound buffer object's contents that are linked to vertex attributes in the GPU when using `glVertexAttribPointer()`. 

Switching out the currently bound buffer in the internal state using e.g. `glBindBuffer(GL_ARRAY_BUFFER, vbo2_ID)` does **not** deallocate `vbo1`'s part of the GPU memory, it simply tells OpenGL to now look at `vbo2` instead whenever performing an operation that uses the currently bound buffer. The switch back can be made at any point.

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)
[🌐 ChatGPT - How does the definition of OpenGL object apply to VBOs?](https://chatgpt.com/s/t_690893d47e1881918885bc83590d4080)