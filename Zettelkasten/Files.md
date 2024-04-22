202403300506
Status: #idea
Tags: 

# Files

*Files* are simply sequences of bytes. They serve as the operating system's abstraction of I/O devices in computers. This abstraction allows application programs to communicate (input and output) in a uniform and reliable way with many varying kinds of I/O devices, without having to accomodate each kind individually and worry about how the device is implemented in hardware. 

For example, a program whose purpose is to take input from a camera and output it to the screen does not see "*a camera*" as an input source per se, but rather sees sequences of bytes representing the image frames coming in — it sees *files*. So in writing this program, we need not tell it how to deal with "*cameras*," but rather how to deal with the *files* it takes as input. 


___
# References
[[📕 Computer Systems - Bryant, O'Hallaron]]