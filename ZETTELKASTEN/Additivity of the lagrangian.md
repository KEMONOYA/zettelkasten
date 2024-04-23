202404232123
Status: #idea
Tags:

# Additivity of the lagrangian

The [[Lagrangian]] has the property of being additive for noninteracting parts of a system. That is, if a mechanical system is composed of two parts $A$ and $B$ which would have lagrangians $L_A$ and $L_B$ respectively if closed, then the limit of the whole system's lagrangian $L$ as the distance between the parts increases so much that they don't interact becomes 
$$\lim L = L_{A}+ L_B.$$
This property implies that **each of the noninteracting parts' equations of motion cannot contain quantities pertaining to the other part**. Why? Because if for example $B$ did contain quantities pertaining to $A$, then the additive property implies that the equation of motion for a quantity from $A$ obtained from the lagrangian $L_A$ differs from the equation obtained from the lagrangian of the whole system $L$. This cannot be if the two parts are truly noninteracting and do not affect one another. 

To see this more clearly, let's try using [[Lagrange's equations]] with each lagrangian to write down the equation of motion for some quantity $x_A$ pertaining to $A$. In the case of $L_A$ we obtain the equation of motion by $$\frac{\partial L_A}{\partial x_{A}}- \frac{d}{dt}\frac{\partial L_A}{\partial \dot x_{A}}= 0.$$ But in the case of $L = L_{A}+ L_B$, we get 
$$\frac{\partial L}{\partial x_{A}}- \frac{d}{dt} \frac{\partial L}{\partial \dot x_{A}}= 0,$$
which, by linearity of the derivative, expands to 
$$ \left(\frac{\partial L_A}{\partial x_{A}}- \frac{d}{dt} \frac{\partial L_A}{\partial \dot x_{A}}\right) + \left(\frac{\partial L_B}{\partial x_{A}}- \frac{d}{dt} \frac{\partial L_{B}}{\partial \dot x_{A}}\right) = 0.$$
Now if the equation of motion in part $B$ contains no instances of $x_A$, which pertains to $A$, then the terms in the second bracket above should all vanish, and the equation of motion reduces to just the $L_A$ part, giving us the same equation as when we used only $L_A$ to obtain the equation. On the other hand, if part $B$ actually does contain $x_A$, then we see that the second bracket doesn't reduce to zero, and instead adds something to the $L_A$ part, giving us a different equation that the one we got with $L_A$. This would mean the equation governing the motion of $x_A$ differs when we view $A$ as a closed system of its own, and when we view it as part of a system in which it interacts with no other parts. Evidently, however, these two cases should be the exact same. Hence, the equations of motion of one part among the noninteracting parts cannot include quantities pertaining to the other.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], p.4.