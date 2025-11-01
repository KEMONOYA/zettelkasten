202511011304
Status: #idea
Tags: [[Graphics programming]]

# Graphics pipeline

> The *graphics pipeline* of OpenGL is a series of steps that takes as input 3D coordinates, and transforms them into colored 2D pixels on the screen. It can be roughly split into two stages, the first is transforming the 3D coordinates into 2D coordinates, and the second is transforming those 2D coordinates into 2D colored pixels on the screen.
![[graphics_pipeline.png]]
* *Some of these (marked in blue) are configurable by the developer, allowing full control over the details of how they operate.* 

Each of these steps is highly specialized (each performing only one specific function), and the programs actually carrying out each of these functions are called [[shader]]s.

___
# References
