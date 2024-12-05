202412032305
Status: #idea
Tags: [[Reverse engineering]]

# Pointer scanning in Cheat Engine

Say we've found a health variable's *dynamic* address in Assault Cube and we want to find a *static* (multi-level) pointer to it, so that we can keep track of its changing dynamic address whenever we restart the game. How do we go about this?

There are multiple ways to find a reliable pointer path, and they vary in efficiency. Let's take a look at each.

1. **Finding its entity object through functions that access it (aka. the manual way)**

The first thing we might try is to scan for addresses that contain the health's address as their value (pointers to health variable) straightaway. If we do this in Assault Cube, we actually get no results back. Does this mean that no pointers at all point to the health? Not quite. It means that no pointers point *directly* (in one step) to the health. But if that's the case, how else can we find a pointer path to the health? Well, one way to get around this is to find a variable/address that (1) *does* have a direct static pointer to it, and (2) we can reliably write the health address as an *offset* of this variable in question every time the game starts.

A good candidate for such an address is the address of the localPlayer entity (*entity* here referring to an instance of a class), of which health is an attribute (we assume the existence of this entity, but it's a good guess because that's just how any decent object-oriented programmer would do it). We can further guess that whenever a function accesses the health, it does so as an attribute of the localPlayer (e.g. localPlayer.health). This is because the dynamic address of the health is ever-changing so the instruction needs a reliable address (one offset from a static pointer) with which to reach the health (here we again make an assumption that we can find some static pointer to localPlayer).

We can use the above assumptions to help us find a static pointer to the localPlayer, and as an offset to it, to the health as well. Cheat Engine has a nice feature that allows us to see what code accesses (reads/writes to) any given variable. Using this on the health we've found will show us some code that accesses health. For extra measure, we can damage ourself in-game to execute some code that *writes* to the health, so we have more to work with. Now in this code, we'll see our health written as an offset from some different addresses (see image below), each of which is a candidate for the localPlayer entity object, and we wish to figure out which one it is. 

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
4. Compare the two pointermaps to keep only the pointers that are common between the two, and point to the health address in both pointermaps, wherever it may be (will probably be different in the first and second cases, since we restarted the game, but the pointer's *static* address is the same)

Here's how to use this method, in more detail:
First, we find a (dynamic) address for our health variable. Next, we generate a pointermap. Now we don't scan right away, we just restart the game, which causes a lot of the pointers in the game's memory to change what they're pointing to, most of them will now point to random stuff. (**We know however that the consistent reliable pointer that we're looking for will point to the new health address again, wherever it may be**). 

Anyways, having loaded the game again, we again scan for the (dynamic) health address, which will be different than the first. We again right-click it and generate a new pointermap. Now, we right-click it again and choose to "Pointer scan for this address." Here's where the magic happens. We choose to use a saved pointermap, and pick the second pointermap we generated. But we also choose to compare to "**Compare results with other saved pointermap(s).**" We then load the first pointermap we generated, and let it scan for the *first* health address we got before we restarted the game. 

This basically scans `Pointermap2` for `HealthAddr2`, and scans `Pointermap1` for `HealthAddr1`, and then takes the intersection of the two resulting tables. This works because whatever reliable pointers we had in `Pointermap1` pointed to the health address at the time, `HealthAddr1`, and since they're reliable, they will point to `HealthAddr2` once we've restarted the game, which is reflected in `Pointermap2`. So they will be the pointers that show up in both scans, and hence the intersection.

This method generally generates much fewer and more accurate results than the previous method, and in less steps, so it is preferred. But note that we have no reason to stop here, and we can narrow down the results further using the same filters we used in the previous method. In particular, we can
1. Specify the ending offset
2. Specify the range of the base address (the base module)

Refer back to the previous method for instructions on how to do these.

___
# References
[🎞️ How To Find Offsets, Entity Addresses & Pointers](https://www.youtube.com/watch?v=YaFlh2pIKAg&feature=youtu.be)
[🎞️ Cheat Engine How to Pointer Scan with Pointermaps 🚨](https://www.youtube.com/watch?v=nQ2F2iW80Fk)
[🤖 Pointermap **Overview** CE](https://chatgpt.com/c/674f8a2d-95d4-800d-96f3-616a3080e00d)