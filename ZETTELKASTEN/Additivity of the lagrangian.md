202404232123
Status: #idea
Tags: [[Mechanics]]

# Additivity of the lagrangian

The [[Lagrangian]] has the property of being additive for noninteracting parts of a system. That is, if a mechanical system is composed of two parts $A$ and $B$ which would have lagrangians $L_A$ and $L_B$ respectively if they were closed, then the limit of the whole system's lagrangian $L$ as the distance between the parts increases so much that their interaction may be neglected becomes 
$$\lim L = L_{A}+ L_B.$$

What the additive property is saying is that 'isolated' mechanical systems are not to be considered as having their own lagrangians in isolation, but rather to be considered as disjoint parts of a "bigger" lagrangian that just happens to approach the sum of the hypothetical closed lagrangians of each of the parts as the distance between them approaches infinity. It's emphasizing that truly isolated systems do not exist, and that all systems are just parts of the "universe lagrangian". This is especially important when discussing the [[Multiplication of the lagrangian by a constant]].

This property also expresses the fact that **each of the noninteracting parts' equations of motion cannot contain quantities pertaining to the other part**, as this is *only possible* if the lagrangian of the combination is the sum of the lagrangians of the parts. This is due to linearity of the derivative, which guarantees that we can separate the equations of motion of each part in Lagrange's equations like we see below, and avoid getting quantities of one part involved in the equations of the other part's quantities. 

$$\left(\frac{\partial L}{\partial x}-\frac{d}{dt}\frac{\partial L}{\partial \dot x}\right) = 0,$$
and expanding $L$, we get
$$\left( \frac{\partial L_A}{\partial x}- \frac{d}{dt} \frac{\partial L_A}{\partial \dot x} \right) + \left( \frac{\partial L_B}{\partial x} - \frac{d}{dt} \frac{\partial L_B}{\partial \dot x} \right) = 0.$$
We see therefore that if $x$ is a quantity of part $A$, then the $B$ terms all zero out in the equation above and we're left with the same equation of motion we get for $x$ if we're working with $A$ as a closed system, devoid of any quantities from part $B$.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.4.