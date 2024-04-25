202404232123
Status: #idea
Tags:

# Additivity of the lagrangian

The [[Lagrangian]] has the property of being additive for noninteracting parts of a system. That is, if a mechanical system is composed of two parts $A$ and $B$ which would have lagrangians $L_A$ and $L_B$ respectively if closed, then the limit of the whole system's lagrangian $L$ as the distance between the parts increases so much that they don't interact becomes 
$$\lim L = L_{A}+ L_B.$$
This property is derived from the fact that **each of the noninteracting parts' equations of motion cannot contain quantities pertaining to the other part**, as this is *only possible* if the lagrangian of the combination is the sum of the lagrangians of the parts. This is due to linearity of the derivative, which guarantees that we can separate the equations of motion of each part in Lagrange's equations like we see below, and avoid getting quantities of one part involved in the equations of the other part's quantities. 

$$\left(\frac{\partial L}{\partial x}-\frac{d}{dt}\frac{\partial L}{\partial \dot x}\right) = 0,$$
and expanding $L$, we get
$$\left( \frac{\partial L_A}{\partial x}- \frac{d}{dt} \frac{\partial L_A}{\partial \dot x} \right) + \left( \frac{\partial L_B}{\partial x} - \frac{d}{dt} \frac{\partial L_B}{\partial \dot x} \right) = 0.$$
We see therefore that if $x$ is a quantity of part $A$, then the $B$ terms all zero out in the equation above and we're left with the same equation of motion we get for $x$ if we're working with $A$ as a closed system, devoid of any quantities from part $B$.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.4.