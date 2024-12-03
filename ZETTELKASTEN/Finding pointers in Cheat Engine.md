202412032236
Status: #idea
Tags: [[Reverse engineering]]

# Finding pointers in Cheat Engine

Say we've found a health variable's address in Cheat Engine and we want to find a pointer path to it starting from the module base, so we can reliably access the health variable whenever we restart the game. How do we go about this? *(Note that we will use Assault Cube 1.2.0.2 as our example)*

There are two main methods, varying in efficiency:

1. **Tracing back a path from instruction calls that access our variable.** Cheat Engine allows us to see which instructions access our health variable, and the useful thing about that is that those instructions do not access the health variable directly, but rather access it as an offset from the entity object that it's a part of (in our example, the localPlayer entity). 
Let's try this

___
# References
