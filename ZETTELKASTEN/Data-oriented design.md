202502161858
Status: #idea
Tags: [[Software engineering]]

# Data-oriented design

Data-oriented design (DOD) describes writing programs in a way that is very conscious of how its data should be stored in memory, caches and registers, maximizing time-efficiency in retrieving and maniplating data. This approach is very useful when designing real-time systems like game engines and interactive physics simulations, which needs to work with large amounts of data in very small time-frames.

Unlike OOP, DOD does not describe a kind of blueprint for designing programs, but instead is more general in its meaning, referring generally to optimizing programs' memory storage and access. This includes understanding how much memory can be stored in CPU caches (L1, L2, L3), how fast the CPU can access each cache, how long it takes the CPU to retrieve data from main memory and store it in L3 and how much data it can retrieve at once, etc.
All this can be taken into account to bring as much needed data to the CPU as possible, in as little time as possible, using caches to their full potential with as little wasted space as we can get (See the first link in *References* for a more detailed look at memory caches and various ways to optimize code for them).

___
# References
[🌐 Intro to Data Oriented Design for Games](https://www.youtube.com/watch?v=WwkuAqObplU)
[🌐 Data-Oriented Design: The Future of Game Development](https://www.youtube.com/watch?v=wG2Y42qArHY)