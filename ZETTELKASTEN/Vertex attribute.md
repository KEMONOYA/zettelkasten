202511012218
Status: #idea
Tags: [[Graphics programming]]

# Vertex attribute

> A *vertex attribute* is an attribute of a [[vertex]] that we can choose to include in the vertex data. These attributes are defined by the programmer in the [[vertex shader]] code they choose to use, in the form of inputs to the shader. Examples of these attributes are *3D position* and *color*.

When defining vertex data in code, which runs on the CPU, to then later be passed to the GPU, we do so by just writing the data we want, in the order we want, in a vertex data array. [[Vertex]]es however carry many kinds of information; take for instance position and color. When we pass a vertex data array to the GPU, it has no idea how you chose to 'format' the vertex data; it knows which attributes you defined, but in what order should it assign them values from your data? where does the data of each attribute start and end? how big is the gap between one vertex and another in the array for the same attribute?

For this reason, we have to specify for the GPU a 'model' of sorts for what it should expect vertex data to be formatted like so it knows how to read it.

## Practical example
Here's an example of how we would actually do all of this in code.
#### 1. Define the needed attributes as inputs to the [[vertex shader]].

```c++
const char *vertexShaderSource = "#version 330 core\n"
    "layout (location = 0) in vec3 aPos;\n"
    "void main()\n"
    "{\n"
    "   gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0);\n"
    "}\0";
```
Here it can be seen we defined only one attribute (input) `vec3 aPos`, the 3D position of the vertex. This means we expect each vertex in the vertex data to be a 3-tuple describing only its position. Notice also the `layout (location = 0)` preceding the attribute. This assigns it an index of 0 amongst the attributes defined in the GPU, which we will later use to refer to it by when assigning values to attributes.

#### 2. Define your vertex data.

```c++
GLfloat vertices[] =
{
	-0.5f, -0.5f, 0.0f,
	 0.5f, -0.5f, 0.0f,
	 0.0f,  0.5f, 0.0f
};
```
As we configured above, we define the vertices as triplets of values, each describing the 3D position of the vertex. Notice that until we actually link these values to the attributes, this array has no meaning or interpretation (in fact, nothing even specifies that these are *triplets* yet), and is nothing more than a list of floats.

#### 3. Link vertex data to vertex attributes.

Now we finally link the vertex attributes to the vertex data, by telling OpenGL how it should interpret the data inside the current [[vertex buffer object]]. We do this using the method `glVertexAttribPointer()`.
___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)