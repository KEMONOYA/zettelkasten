202405191655
Status: #idea
Tags: [[Mechanics]]

# Mechanical similarity

Mechanical similarity is a technique that applies to some mechanical systems, using which we can make inferences about the behavior of the system without even integrating the equations of motion. It is based on the fact that the equations of motion are unaffected under [[multiplication of the lagrangian by a constant]].

Namely, mechanical similarity applies in systems where the potential energy $U$ is a homogeneous function. In such systems, it allows us to **determine *ratios between the mechanical quantites* (time taken, momentum, energy, etc.) of two paths in the system that are geometrically similar but different in size, *as powers of the ratio between the lengths* *of the two paths***. So for instance, in a system where a particle revolves around the origin in a circle in a fixed plane, mechanical similarity can be used to determine
- a ratio between the time taken for a particle to revolve a circle of radius $r=1$ and another of radius $r=2$
- a ratio between the angular momenta of those two particles, [at corresponding points on their paths, at corresponding times](obsidian://open?vault=Vaults&file=Monologue%2FZETTELKASTEN%2FConservation%20of%20proportions%20under%20scaling%20paths%20of%20homogeneous%20potentials)
- a ratio between the linear momenta of the particles
- a ratio between the energies of the particles
- etc.
each as a power of the ratio of the dimensions of the two paths. So if the two paths are circles of radii $r=1$ and $r=2$, then each of the ratios above can be written as a power of the ratio $l^\prime/l=(2\pi\cdot2)/(2\pi\cdot1)=2$. 

The main advantage of this tool is not, however, to use it for numerical computations. Rather, we can use these ratios to make inferences about the behavior of the system in general. To see how this is done, we first need to establish exactly how to find these ratios as powers of $l^\prime/l$.

Assume $U$ is a homogeneous function of degree $k$. If we scale the linear dimensions by $\alpha$,
$$\textbf r_{a}\to \alpha \textbf r_a,$$
then the potential $U$ is scaled by $\alpha^k$. 

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pgs. 22, 23.