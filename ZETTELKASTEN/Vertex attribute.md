202511012218
Status: #idea
Tags: [[Graphics programming]]

# Vertex attribute

> A *vertex attribute* is an attribute of a [[vertex]] that we can choose to include in the vertex data. These attributes are defined by the programmer in the [[vertex shader]] they choose to use, in the form of inputs to the shader. Examples of these attributes are *3D position* and *color*.

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
As we configured above, we define the vertices as triplets of values, each describing the 3D position of the vertex. Notice that until we actually link these values to the attributes, this array has no meaning or interpretation (in fact, nothing even specifies that these are *triplets* yet), and is nothing more than a list of floats. This array's data will be loaded into a [[vertex buffer object]] which is then bound to the `GL_ARRAY_BUFFER` slot, so that any time in the future we refer to the currently bound `GL_ARRAY_BUFFER` we'll be working with our *VBO*. 

#### 3. Link vertex data to vertex attributes.

Now we finally link the vertex attributes to the vertex data, by telling OpenGL how it should interpret the data inside the current [[vertex buffer object]] (*VBO*). We do this using the method
```c++
glVertexAttribPointer(GLuint index, GLint size, GLenum type, GLboolean normalized, GLsizei stride, const GLvoid* pointer)
```

This method tells each attribute where to look for its values in the current *VBO*. The parameters it needs are as follows:
- `GLuint index`: the index of the attribute we want to link in the vertex shader. Recall above how we specified `layout (location = 0)` for the position, so if we want to assign the position values, we'd use index 0.
- `GLint size`: specifies how many components (elements of the *VBO* array) this vertex attribute should take; must be 1, 2, 3 or 4. So for instance, our 3D position attribute, being a `vec3` would expect three floats, so size = 3.
- `GLenum type`: the data type it should expect for the values of its components. In our case, that would be a float, which in this enum is specified by `GL_FLOAT`.
- `GLboolean normalized`: specifies whether the data should be normalized, i.e. clamped to \[-1,1] for signed values, or \[0,1] for unsigned values.
- `GLsizei stride`: specifies the distance between the *start* of one instance of this vertex attribute and the *start* of the next instance. So if we have 2 vertices defined in the *VBO*, this specifies how much to move a pointer from the start of the position attribute of one vertex to get to the position attribute of the next.
- `GLvoid* pointer`: specifies an offset (*in bytes) from the start of the *VBO* array to get to the first instance of this attribute in the first vertex defined. Note that whatever number you set this to, you need to cast it into a `void*` first for the function to accept it. So if I wanted 4 bytes, I'd do `(void*) 4`.

**One more thing to notice** is that we never specified here the array from which it should read our vertex data in the first place. This is because vertex attributes take their values from the *VBO* bound to `GL_ARRAY_BUFFER` at the time of calling `glVertexAttribPointer()` (*see the end of step 2*).

Now that we know what it does, let's apply it to our case, and link the `vec3 aPos` attribute to the data we have in the *VBO* currently bound to `GL_ARRAY_BUFFER`:
```c++
glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
glEnableVertexAttribArray(0);
```
Note that **vertex attributes are disabled by default**, so we call `glEnableVertexAttribArray()` with the index of the `aPos` attribute to enable it.

With this, we have formatted our vertex buffer data correctly, and it should now look like this from the perspective of the GPU:
![[vertex_attribute_pointer.png]]

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)