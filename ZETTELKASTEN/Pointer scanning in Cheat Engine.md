202412032305
Status: #idea
Tags: [[Reverse engineering]]

# Pointer scanning in Cheat Engine

Say we've found a health variable's *dynamic* address in Assault Cube and we want to find a *static* (multi-level) pointer to it, so that we can keep track of its changing dynamic address whenever we restart the game. How do we go about this?

There are multiple ways to find a reliable pointer path, and they vary in efficiency. Let's take a look at each.

1. **Tracing back a path through its entity object (aka. the manual way)**

The first thing we might try is to scan for addresses that contain the health's address as their value (pointers to health variable) straightaway. If we do this in Assault Cube, we actually get no results back. Does this mean that no pointers at all point to the health? Not quite. It means that no pointers point *directly* (in one step) to the health. But if that's the case, how else can we find a pointer path to the health? Well, one way to get around this is to find a variable/address that (1) *does* have a direct static pointer to it, and (2) we can write the health address as an *offset* of this variable in question.

It's reasonable to assume the health variable is part of a localPlayer entity object in the game's code. For this reason, we can also assume that when any game code accesses this health variable, it does that through the player object, as an attribute (*e.g.* it might be accessed as Player.health in the game code). We can use this fact to help us reach the entity object's address. Cheat Engine has a nice feature that allows us to see what code accesses (reads/writes to) any given variable. Using this on the health we've found will show us some code that accesses health. For extra measure, we can damage ourself in-game to execute some code that *writes* to the health, so we have more to work with. Now in this code, we'll see our health written as an offset from some different addresses (see image below), each of which is a candidate for the localPlayer entity object, and we wish to figure out which one it is. 

![[instructions.png]]

One way to figure out which one is the localPlayer entity is to perform data/structure dissection on each, from the Memory View window of Cheat Engine, and see which of them displays values relevant to the player (health, ammo, coordinates, etc...). Once we figure out which one it is, we can perform another scan on its address to see if any static pointers point to it. Lo and behold, we do find static addresses (indicated in green in the scan results) pointing to the localPlayer entity. With this, we are basically done, because we now have a reliable path to the health variable as follows:
`[<ac_client.exe> (module base) + offset1] + offset2`
where `offset1` is the offset of the *pointer* to localPlayer from the module base (this is found from the static address we just found above), and `offset2` is the offset of the health variable from the localPlayer base (this is found from the code accessing the health as in the image above. So examples would be `F8` or `04`).

**This method is in general not very effective, especially in newer games where getting from the static address to the health might be much more complicated than a single offset.**


2. **Pointer scanning using a single pointermap (aka. the traditional method)**

The first method discussed above is fairly accurate (as in, provides a logical, consistent pointer) when it does work, but the problem is that it's very likely that the path from the module base to your health variable is not as simple as the one discussed above. In other words, it might contain more than one offset, which means you'll have to trace back through multiple objects and offsets (and each one of these object/offset pairs, you don't even know their addresses for sure, so you'll be making several hypotheses at a time, which is a crazy number of possibilities to try out by hand.)

A more general and reliable method is needed for finding pointers, then. For this purpose, we  

___
# References
