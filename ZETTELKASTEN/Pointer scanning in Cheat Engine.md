202412032305
Status: #idea
Tags: [[Reverse engineering]]

# Pointer scanning in Cheat Engine

Say we've found a health variable's *dynamic* address in Assault Cube and we want to find a *static* (multi-level) pointer to it, so that we can keep track of its changing dynamic address whenever we restart the game. How do we go about this?

There are multiple ways to find a reliable pointer path, and they vary in efficiency. Let's take a look at each.

1. **Tracing back a path through its entity object.**
The first thing we might try is to scan for addresses that contain the health's address as their value (pointers to health variable) straightaway. 
It's reasonable to assume the health variable is part of a localPlayer entity object in the game's code. For this reason, we can also assume that when any game code accesses this health variable, it does that through the player object, as an attribute (*e.g.* it might be accessed as Player.health in the game code). We can use this fact to help us reach the entity object's   


___
# References
