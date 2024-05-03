202405021441
Status: #idea
Tags: [[Mechanics]]

# Energy

Energy is a numerical quantity that does not change over time in a closed mechanical system. It is an abstract quantity that has no concrete physical picture, it is merely a quantity. It has the form 
$$ E = T+U,$$
where $T$ is the [[kinetic energy]], and $U$ is the [[potential energy]] of the system. (See below for derivation)

It comes in various forms (kinetic, gravitational potential, heat, electrical, nuclear, etc.), each with its own formula, and energy in a system may change between these forms over time, but its total quantity is nonetheless conserved. Meaning if we sum up the contributions of each form of energy in a system at any point in time, we'll always end up with the same total. It is this conservation that makes energy special, and worth our attention, because it means energy serves as a [[conserved quantity]], whose additive property makes it extremely useful in studying interactions in mechanical systems.

#### Derivation

Conservation of energy (which also practically provides the definition of energy itself, reflecting the fact that the conservation property *is* what makes energy worth studying) is derived from the fundamental [[homogeneity of time]] in [[inertial frame]]s. By virtue of this homogeneity, the [[lagrangian]] of a closed system does not depend explicitly on time. As a result, the total time derivative of the lagrangian is
$$\frac{dL}{dt} = \sum \frac{\partial L}{\partial x_{i}}\dot x_{i}+ \sum \frac{\partial L}{\partial \dot x_{i}} \ddot x_i.$$
Substituting $\partial L/\partial x_{i} = ({d}/{dt}) \partial L /\partial \dot x_i$, we get
$$\frac{dL}{dt}= \sum \frac{d}{dt} \frac{\partial L}{\partial \dot x_{i}} \dot x_{i}+ \sum\limits \frac{\partial L}{\partial \dot x_{i}}\ddot x_{i}= \frac{d}{dt}\sum\limits\frac{\partial L}{\partial \dot x_{i}}\dot x_i,$$
which finally gives us
$$\frac{d}{dt}\left(\sum\limits\frac{\partial L}{\partial \dot x_{i}}\dot x_{i}-L\right) = 0,$$
so the quantity
$$E \equiv \sum\limits\frac{\partial L}{\partial \dot x_{i}}\dot x_{i}-L=\text{constant.}$$
This quantity $E$ is the *energy* of the system. Substituting in $L = T-U$, the first term above becomes $\sum\limits (\partial T /\partial \dot x_{i}) \dot x_i$ and using [[Euler's homogeneous function theorem]] on that term above, we see that 
$$E = 2T+U-T=T+U.$$
So the energy is the sum of two quite different terms, a function of the velocities and a function of coordinates.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.14.
[🌐 The Feynman Lectures on Physics Vol. I Ch. 4: Conservation of Energy](https://www.feynmanlectures.caltech.edu/I_04.html)