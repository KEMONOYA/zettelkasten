202405191655
Status: #idea
Tags: [[Mechanics]]

# Mechanical similarity

Mechanical similarity is a technique that applies to some mechanical systems, using which we can make inferences about the behavior of the system without even integrating the equations of motion. It is based on the fact that the equations of motion are unaffected under [[multiplication of the lagrangian by a constant]].

Namely, mechanical similarity applies in systems where the [[potential energy]] $U$ is a homogeneous function. In such systems, it allows us to **determine *ratios between the mechanical quantites* (time taken, momentum, energy, etc.) of two paths in the system that are geometrically similar but different in size, *as powers of the ratio between the lengths* *of the two paths***. So for instance, in a system where a particle revolves around the origin in a circle in a fixed plane, mechanical similarity can be used to determine
- a ratio between the time taken for a particle to revolve a circle of radius $r=1$ and another of radius $r=2$
- a ratio between the angular momenta of those two particles, [at corresponding points on their paths, at corresponding times](obsidian://open?vault=Vaults&file=Monologue%2FZETTELKASTEN%2FConservation%20of%20proportions%20under%20scaling%20paths%20of%20homogeneous%20potentials)
- a ratio between the linear momenta of the particles
- a ratio between the energies of the particles
- etc.
each as a power of the ratio of the dimensions of the two paths. So if the two paths are circles of radii $r=1$ and $r=2$, then each of the ratios above can be written as a power of the ratio $l^\prime/l=(2\pi\cdot2)/(2\pi\cdot1)=2$. 

The main advantage of this tool is not, however, to use it for numerical computations. Rather, we can use these ratios to make inferences about the behavior of the system in general. To see how this is done, we first need to establish exactly how to find these ratios as powers of $l^\prime/l$.

Assume $U$ is a homogeneous function of degree $k$. If we scale the linear dimensions by $\alpha$,
$$\textbf r_{a}\to \alpha \textbf r_a,$$
then the potential $U$ is scaled by $\alpha^k$. If we also scale the time by $\beta$, the velocity $d\textbf r_a/dt$ is then scaled by $\alpha/\beta$, and the kinetic energy by $(\alpha/\beta)^2$. If we pick $\beta$ such that $\alpha^{k} = (\alpha/\beta)^2$, i.e. $\beta = \alpha^{1-\frac{1}{2}k}$, then $a^k$ can be pulled out of both $T$ and $U$ in the lagrangian, and so the lagrangian after scaling is just the original lagrangian multiplied by a constant, and hence our transformation has no effect on the equations of motion.

Scaling the coordinates like we did above corresponds to scaling the paths of motion, producing geometrically similar paths of the same shape but varying sizes. Thus we see that when $U$ is a homogeneous function, the equations of motion permit a series of geometrically similar paths, and the ratio between the times of corresponding points on the paths is
$$\frac{t^{\prime}}{t}= \left(\frac{l^{\prime}}{l}\right)^{1-\frac{1}{2}k}.$$
The ratio of any other mechanical quantity at corresponding points can likewise be written as a power of $l^{\prime}/l$. For example, 
$$\frac{v^{\prime}}{v}=\left(\frac{l^{\prime}}{l}\right)^{\frac{1}{2}k},\hspace{0.7cm} \frac{E^{\prime}}{E}=\left(\frac{l^{\prime}}{l}\right)^{k}, \hspace{0.7cm} \frac{M^{\prime}}{M}=\left(\frac{l^{\prime}}{l}\right)^{1+\frac{1}{2}k} .$$

With all this established, we can make some important inferences.

- In small oscillations, the potential energy $U$ is a quadratic function of the coordinates (i.e. $k=2$), so from the above relation between time and linear dimensions, the period of small oscillations is independent of their amplitudes.
- In uniform fields of force, the potential energy is a linear function of the coordinates (i.e. $k=1$). So it follows that, in free fall under gravity for example, the time taken is proportional to the square root of the initial height above the ground.
- In the Newtonian attraction of two masses, or the Coulomb interactions of two charges, the potential energy is inversely proportion to the distance apart (i.e. $k=-1$). Therefore, we find that $t^{\prime}/t = (l^\prime/l)^{3/2}$. From this, we can state that the square of time of revolution is proportional to the cube of the size of the orbit. This is *[[Kepler's third law]].*

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pgs. 22, 23.