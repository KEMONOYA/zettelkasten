202511031340
Status: #idea
Tags: [[Graphics programming]]

# OpenGL object

> An *OpenGL object* is a collection of options (state variables) that encapusulates a subset of OpenGL's state.

To understand this definition fully, we have to understand that **OpenGL is a state machine**.
That means at any given moment, it stores an internal configuration (a *state*) that dictates how drawing functions in the GPU will behave.

Examples of these state variables are:
- Which shader program is active?
- Which texture is bound to texture unit 0?
- Which buffer provides vertex data?
- What blending mode or depth test is enabled?



___
# References
