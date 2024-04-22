202403281946
Status: #idea
Tags: [[Compilation]]

# Assembly phase

The third phase of the compilation of a computer program. Translates the assembly-language source file generated in the [[Compilation phase]] into a set of machine-instructions, packages them in a form known as a *relocatable object file*, and stores the result in a file with the `.o` suffix. This resulting `.o` file is a binary file, not a [text file](ASCII%20standard.md). That is, if you were to view the file in a text editor, it would appear to be gibberish because its bytes no longer encode characters, but rather machine language instructions.

So for instance if the assembler took as input a *text* file `hello.s`, it would output a *binary* file `hello.o`. 


___
# References
[[📕 Computer Systems - Bryant, O'Hallaron]]
