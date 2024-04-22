202403281931
Status: #idea
Tags: [[Compilation]]

# Preprocessing phase

The first phase in the compilation of a computer program. This phase handles substitutions into the source code file, marked (in C, for example) by the # symbol. For instance, in

```c 
#include <stdio.h>

int main()
{
	printf("hello, world\n");
}
```

the `#include <stdio.h>` line tells the preprocessor the read the contents of the file `stdio.h` and insert them directly, as text, into this source code file. The result is another C source file with the inserted contents, typically with the `.i` suffix. So if this file were called `hello.c`, the preprocessor would output `hello.i`.

___
# References
[[📕 Computer Systems - Bryant, O'Hallaron]]
