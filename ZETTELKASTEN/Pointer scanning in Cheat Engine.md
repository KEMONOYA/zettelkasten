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

A more general and reliable method is needed for finding pointers, then. For this purpose, we make use of Cheat Engine's pointer scanning feature. We can scan for pointers pointing to a given address in our address list by right-clicking it and choosing "Pointer scan for this address." **However,** an important note to make regarding how Cheat Engine handles pointer scanning. When you execute a pointer scan, Cheat Engine first generates a *pointer map*, which is a list containing **every single pointer in the game process's memory at the time of capture.** Then, CE narrows this list down to only pointers pointing to your desired address. The reason CE has to do this is because pointer paths might be complicated and go through several steps before reaching the desired address, so in order to make sure all such paths are accounted for, it has to scan everything.

In our process of getting the pointer we want though, we're going to have to perform multiple scans to narrow down our results. But if we just use the scanning feature normally like discussed above, then CE will generate a pointer map every single time, which is very inefficient. What's a better way to go about scanning? Well, we generate the pointer map in advance, and tell CE to use that pointer map every time it performs the scan. We can do this easily by right clicking the address in our address list and clicking "Generate pointermap."
Then whenever we scan, we can tick the checkbox labeled "Use saved pointermap" and load the one we generated in advance.

With that out of the way, we now have a list of pointers pointing to the correct address, but we still have thousands of results to sift through. We can narrow this down further.
First, we can click on "Pointer scanner" at the top and choose "Rescan memory - ...", this allows us to rescan the same list and narrow it down. We input the address (or value) we want to scan for again, and we can now add some extra options to eliminate some undesired results.
1. **Use the "Base pointer must be in range" option.** If we know that the base address is going to start in 'ac_client.exe' for example, then we can indicate exactly where 'ac_client.exe' starts in the process's memory, and where it ends, to narrow the results down to just these. To find the address of 'ac_client.exe', we can go back to CE and click "Add Address Manually," then in place of the address use the following CE script: `getAddress('ac_client.exe')`. This will give the start address of the base module. To get the end address, we add another address with the script: `getAddress('ac_client.exe') + getModuleSize('ac_client.exe')`.
2. **Specify the ending offset.** We can usually, by using the "Find out what accesses this address" button, find out what the final offset of our variable is going to be. For instance, in the image above, we see it's either going to be `F8` or `04`. We can specify this in the scan settings so we narrow down further.
3. **Restart the game.** When we restart the game, some pointers that initially pointed to the correct address by mere chance will have changed, but the valid pointers stay valid. We can use this fact to reduce our list further, by restarting the game (keeping the list open), and rescanning once it's open again, specifying the new address (or value) of the health variable, and the final offset. (You no longer need specify the base pointer range because it's already been narrowed down to only 'ac_client.exe', it's a one-time thing).

Repeating this refinement of the list over and over will leave us with maybe a couple hundred results in the end. That's about as good as this scanning method can do. There is still a way to refine the list further however, which is discussed in the next method.


3. **Use two pointermaps and compare (aka. the advanced method)**

Despite the name, this method is very similar to the previous one, and is even quicker to perform. The idea of this method is to:
1. Generate a pointermap
2. Restart the game
3. Generate a second pointermap
4. Compare the two pointermaps to keep only the unchanged pointers between the t pointing to our desired address (taking the intersection, basically)


___
# References
