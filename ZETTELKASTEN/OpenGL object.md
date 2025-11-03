202511031340
Status: #idea
Tags: [[Graphics programming]]

# OpenGL object

> An *OpenGL object* is a collection of options (state variables) that encapusulates a subset of OpenGL's state.

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



___
# References
