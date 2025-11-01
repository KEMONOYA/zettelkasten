202511011423
Status: #idea
Tags: [[Graphics programming]]

# Fragment

> A *fragment* in OpenGL is a collection of values produced by the [[rasterization stage]] of the [[graphics pipeline]] that represent data about a single "potential pixel" that may or may not be drawn later on the screen in the [[fragment shader]] stage, depending on the values of this data (*XY position that's checked for clipping, whether it comes from the front or back of a primitive, etc.*).
- *Color data is assigned to a fragment during the fragment shader stage. After this, a fragment may very well still be discarded during its execution of the fragment shader (produces no output), or during later tests. Only surviving fragments after all tests contribute their colors to the screen and become full-fledged rendered pixels.*

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)