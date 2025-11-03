202511031340
Status: #idea
Tags: [[Graphics programming]]

# OpenGL object

> An _OpenGL object_ is a container that encapsulates an instance of a related subset of OpenGL’s state variables, allowing that subset of the GPU state to be stored, modified, replaced and reused.

Generating any *OpenGL object* using `glGenObject(size, &ids)` will store the ID(s) of the generated object(s) in the `GLuint ids[]` array (or just `GLuint id` if generating one object).

To understand the above definition fully, we have to understand that **OpenGL is a state machine**.
That means at any given moment, it stores an internal configuration (a *state*) that dictates how the drawing functions in the GPU will behave.
#### Examples of these state variables are:
- Which shader program is active?
- Which texture is bound to texture unit 0?
- Which buffer provides vertex data?
- What blending mode or depth test is enabled?

Switching out parts of this internal state is done by creating an *OpenGL object* representing that subset, binding it as the currently bound object of its specific type, then setting its values to whatever we want. This switches out the old settings, and the switch back can be done at any time by changing the currently bound object back to the old one.

(*Note: **binding** an object means telling OpenGL's context to point its internal state to that object's instance of the state variables*)
#### So in essence, every command OpenGL carries out is either:
1. change some part of the state (e.g. by binding a different object, thereby changing a part of the behavior of future drawing functions)
2. use the current state to perform an operation (e.g. drawing geometry)

**So, an *OpenGL object* simply represents an *instance* of a subset of related state variables, and allows us to modify those variables, for plugging in to the internal state whenever.**
### Examples of objects include:
- A **buffer object** (like a VBO or EBO) represents the state of a block of GPU memory storing vertex or index data.
- A **texture object** represents all the parameters and data that define a texture (its image, filtering modes, wrapping, etc).
- A **shader program object** represents a compiled and linked set of shaders with their uniform variables.
- A **vertex array object (VAO)** represents all the vertex attribute configuration state.

___
# References
[🌐 ChatGPT - How do objects relate to OpenGL's state?](https://chatgpt.com/s/t_69089e6581088191bdeda5359fb42784)