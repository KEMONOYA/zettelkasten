202502161851
Status: #idea
Tags: [[Game engine]]

# Entity-Component-System (ECS)

**Entity-Component-System (ECS)** is a design pattern for game engines that is [data-oriented](Data-oriented%20design.md), so favors memory-efficiency, and as the name suggests, handles storing and updating game entities using three different parts; entities, components and systems. Let's look at what role each of them plays and how they interact with one another:

1. **Entities**

In ECS, an entity represents any kind of object in the game, such as a character, a tile on a map, a skybox, anything. In terms of implementation, an entity is **nothing more than an ID**. That is, an entity in and of itself has no properties, no shape, nothing. It is merely used as an identifier to link several **components** together into one object, and they are what make up the object and give it all its properties.

2. **Components**

These are what store all information about the entity, including where it is, what it lo

___
# References
[🌐 Game Engine Programming 009 - Identifiers with index and generation parts | C++ Game Engine](https://www.youtube.com/watch?v=rT599NDbkN4&list=PLU2nPsAdxKWQYxkmQ3TdbLsyc1l2j25XM&index=9)
[🌐 Data-Oriented Design: The Future of Game Development](https://www.youtube.com/watch?v=wG2Y42qArHY)