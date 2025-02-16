202502161851
Status: #idea
Tags: [[Game engine]]

# Entity-Component-System (ECS)

**Entity-Component-System (ECS)** is a design pattern for game engines that is [data-oriented](Data-oriented%20design.md), so favors memory-efficiency, and as the name suggests, handles storing and updating game entities using three different parts; entities, components and systems. Let's look at what role each of them plays and how they interact with one another:

1. **Entities**

In ECS, an entity represents any kind of object in the game, such as a character, a tile on a map, a skybox, anything. In terms of implementation, an entity is **nothing more than an ID**. That is, an entity in and of itself has no properties, no shape, nothing. It is merely used as an identifier to link several **components** together into one object, and they are what make up the object and give it all its properties.

2. **Components**

These are what store all information about the entity, including:
- where it is, how it's oriented and how big it is (Transform component)
- what it looks like (Mesh/Material component)
- what its physical properties are (Rigidbody component)
- etc.

3. **Systems**

These are what operate on the components discussed above, and make changes to the entities. For instance, if all entities are affected by gravity, a *System* will loop over all transform components each frame and update their positions accordingly to simulate gravitational pull.


**How are these parts implemented?**

In accordance with data-oriented design, we create an array for each type of component, so that components of the same type are packed together in memory. This helps significantly when we have a System operating on all instances of a specific type of component, like the gravity system mentioned above, since several Transform components will be loaded in the CPU's cache together, making the process very efficient. 

*Entities* are simply indices used to refer to components in their arrays. So, for example, the entity with index 024 will have the Transform component stored at index 024 in the Transforms array, together with the Mesh component stored at 024 in the Meshes array, and so on.

___
# References
[🌐 Game Engine Programming 009 - Identifiers with index and generation parts | C++ Game Engine](https://www.youtube.com/watch?v=rT599NDbkN4&list=PLU2nPsAdxKWQYxkmQ3TdbLsyc1l2j25XM&index=9)
[🌐 Data-Oriented Design: The Future of Game Development](https://www.youtube.com/watch?v=wG2Y42qArHY)