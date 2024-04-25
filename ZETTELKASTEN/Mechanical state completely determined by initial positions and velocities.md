202404222029
Status: #idea
Tags:

# Mechanical state completely determined by initial positions and velocities

When the positions and velocities of all particles of the system are simultaneously specified at some instant, experiment shows that the mechanical state of the system is determined in such a way that the positions of all particles are determined for all subsequent instants in time. That is, all its future motion can, in principle, be calculated.

This may also be stated by saying that the accelerations at that initial instant are determined by the initial positions and velocities. This is equivalent because it means that after an infinitesimal time interval $dt$, the new positions will be known (since the velocities, the changes in positions, were known during the previous instant), and the new velocities will be known (since, as we said, the accelerations, the changes in velocities, were determined by positions and velocities on the previous instant, and hence were known), and therefore on this new instant, again, the positions and velocities are all known, so acceleration is once again determined for this instant. The instant following that is then determined using the same reasoning, and so on for all subsequent instants.

We conclude from this that, concisely, **the acceleration is a function of position and velocity** (and only implicitly a function of time). This is expressed, for instance, in [[Newton's equations]]: $F(x,\dot x, t) = a$.

The above tells us that the motion is completely determined for all future instants, and can be calculated *in principle*. However, to actually reach an expression for the path $x(t)$ and calculate them, the equations of motion in the form $a = F(x, \dot x, t)$ are not sufficient, instead one must integrate them with respect to time. 

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.1.