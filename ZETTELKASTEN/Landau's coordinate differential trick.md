202404272216
Status: #idea
Tags: [[Mechanics]]

# Landau's coordinate differential trick

Often we wish to calculate the quantity $v^2$ for a particle in a mechanical system, to use in the kinetic energy term in the [[lagrangian]] $L = \sum \frac{1}{2}mv^{2} - U(\textbf r).$  Landau provides a trick for writing the expression of $v^2$ in different coordinate systems (cartesian, spherical, cylindrical, etc.). 

Observe that $v^{2}= ({dl}/{dt})^{2}= (dl)^2/(dt)^2$, where $dl$ is an infinitesimal displacement arc length. So if we find $dl^2$, we can just divide it by $dt^2$ to get $v^2$. This is especially handy because infinitesimal displacement elements can always be treated as straight lines, even if their finite counterparts would be curved.

So for example:
- in Cartesian coordinates, $dl^{2}= dx^{2}+ dy^{2}+ dz^2$,    so $L = \frac{1}{2}m(\dot x^{2}+ \dot y^{2} + \dot z^{2})$.
- in cylindrical coordinates, $dl^{2}= dr^{2}+ r^2d\varphi^{2} + dz^2$,    so $L = \frac{1}{2}m(\dot r^{2} + r^{2} \dot \varphi^{2} + \dot z^{2})$.
- in spherical coordinates, $dl^{2}=dr^2+r^2d\theta^2+r^2\sin^2{\theta}d\varphi^2$,    so $L = \frac{1}{2}m(\dot r^{2} + r^{2} \dot \theta^{2} + r^{2} \dot \varphi^{2}\sin^{2}\theta)$.

See below for a figure describing how we find $dl^2$ for cylindrical coordinates, using Pythagoras' theorem. Notice that the small angle approximation for $\sin$ is used in $r d\varphi$.  


![[trick_cylindrical.png]]


___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.8.