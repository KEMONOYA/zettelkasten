202403281958
Status: #idea
Tags: [[Compilation]]

# Linking phase

The fourth, and final, phase of the compilation process of a computer program. Handles merging needed precompiled object files into the input file from the [[Assembly phase]], to allow references to them from the input file. For instance, in the file

```c
#include <stdio.h>

int main()
{
	printf("hello, world\n");
}
```

the function `printf()` is called. This function is part of the C standard library, and resides in a separate precompiled object file called `printf.o`. The linker handles merging this `printf.o` into our compiled `hello.o` to allow this function call. The result is an *executable object file* (or simply *executable*) `hello`, which is ready to be loaded into the memory and executed by the system. 

___
# References
[[📕 Computer Systems - Bryant, O'Hallaron]]