202511011324
Status: #idea
Tags: [[Graphics programming]]

# Vertex shader

> The *vertex shader* is the first part of the [[graphics pipeline]]. It takes as input a single [[vertex]]. 
> Its main purpose is to convert the coordinates of the vertex to *Normalized device coordinates (NDC)*.
>- **Normalized device coordinates**: a coordinate system in which each coordinate takes on only values from \[-1,1], which stretches from one end of the viewport to the other. See figure below.
![[ndc.png]]

Usually, when passing in vertex data to the graphics pipeline, the vertices' coordinates are defined in *object-space coordinates*, which specify the positions of the vertices relative to the local origin of the object they're forming. Then, through various multiplications by different matrices in the vertex shader, these coordinates are transformed into different spaces until they end up in *NDC*.

___
# References
[🌐 LearnOpenGL - Hello Triangle](https://learnopengl.com/Getting-started/Hello-Triangle)