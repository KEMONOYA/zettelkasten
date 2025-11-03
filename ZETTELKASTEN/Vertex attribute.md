202511012218
Status: #idea
Tags: [[Graphics programming]]

# Vertex attribute

> A *vertex attribute* is an attribute of a [[vertex]] that we can choose to include in the vertex data. These attributes are defined by the programmer in the [[vertex shader]] code they choose to use, in the form of inputs to the shader. Examples of these attributes are *3D position* and *color*.

When defining vertex data in code, which runs on the CPU, to then later be passed to the GPU, we do so by just writing the data we want, in the order we want, in a vertex data array. [[Vertex]]es however carry many kinds of information; take for instance position and color. When we pass a vertex data array to the GPU, it has no idea how you chose to 'format' the vertex data; it knows which attributes you defined, but in what order should it assign them values from your data? where does the data of each attribute start and end? how big is the gap between one vertex and another in the array for the same attribute?

For this reason, we have to specify for the GPU a 'model' of sorts for what it should expect vertex data to be formatted like so it knows how to read it.



___
# References
