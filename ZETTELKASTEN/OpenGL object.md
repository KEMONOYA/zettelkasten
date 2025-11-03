202511031340
Status: #idea
Tags: [[Graphics programming]]

# OpenGL object

> An *OpenGL object* is a collection of options (state variables) that encapsulates a subset of OpenGL's state.

To understand this definition fully, we have to understand that **OpenGL is a state machine**.
That means at any given moment, it stores an internal configuration (a *state*) that dictates how the drawing functions in the GPU will behave.

Examples of these state variables are:
- Which shader program is active?
- Which texture is bound to texture unit 0?
- Which buffer provides vertex data?
- What blending mode or depth test is enabled?

Every operation OpenGL performs is either
1. change some part of the state (e.g. by binding a different object to a buffer)
2. use the current state to perform an operation (e.g. rendering)

So, an *OpenGL object* simply represents a subset of related state variables, and allows us to modify those variables.

Examples of objects include:
- A **buffer object** (like a VBO or EBO) represents the state of a block of GPU memory storing vertex or index data.
    
- A **texture object** represents all the parameters and data that define a texture (its image, filtering modes, wrapping, etc).
    
- A **shader program object** represents a compiled and linked set of shaders with their uniform variables.
    
- A **vertex array object (VAO)** represents all the vertex attribute configuration state.

___
# References
[🌐 ChatGPT - How do objects relate to OpenGL's state?](https://chatgpt.com/s/t_69089e6581088191bdeda5359fb42784)