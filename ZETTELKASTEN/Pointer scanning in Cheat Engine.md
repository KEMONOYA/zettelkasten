202412032305
Status: #idea
Tags: [[Reverse engineering]]

# Pointer scanning in Cheat Engine

Say we've found a health variable's *dynamic* address in Assault Cube and we want to find a *static* (multi-level) pointer to it, so that we can keep track of its changing dynamic address whenever we restart the game. How do we go about this?

There are multiple ways to find a reliable pointer path, and they vary in efficiency. Let's take a look at each.

1. **Tracing back a path through its entity object.**
The first thing we might try is to scan for addresses that contain the health's address as their value (pointers to health variable) straightaway. If we do this in Assault Cube, we actually get no results back. Does this mean that no pointers at all point to the health? Not quite. It means that no pointers point *directly* (in one step) to the health. But if that's the case, how else can we find a pointer path to the health? Well, one way to get around this is to find a variable/address that (1) *does* have a direct static pointer to it, and (2) we can write the health address as an *offset* of this variable in question.

It's reasonable to assume the health variable is part of a localPlayer entity object in the game's code. For this reason, we can also assume that when any game code accesses this health variable, it does that through the player object, as an attribute (*e.g.* it might be accessed as Player.health in the game code). We can use this fact to help us reach the entity object's address. Cheat Engine has a nice feature that allows us to see what code accesses (reads/writes to) any given variable. Using this on the health we've found will show us some code that accesses health. For extra measure, we can damage ourself in-game to execute some code that *writes* to the health, so we have more to work with. Now in this code, we'll see our health written as an offset from some different addresses (see below), each of which is a candidate for the localPlayer entity object, and we wish to figure out which one it is. 


___
# References
