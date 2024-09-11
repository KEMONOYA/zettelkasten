202404271323
Status: #idea
Tags: [[Mechanics]]

# Law of inertia

The law of inertia states that in an [[Inertial frame]], any free particle moves with a velocity constant in both magnitude and direction.

###### How do we derive this fact from first principles?
Consider a particle moving freely (i.e. interacts with nothing) in an inertial frame. By [[Homogeneity of space]] and [[Homogeneity of time]], we know the [[Lagrangian]] of this system cannot contain either the coordinate vector $\textbf r$ or the time $t$ explicitly. It is therefore a function of only the velocity $\textbf v$. But also by [[Isotropy of space]], it cannot depend on the direction of $\textbf v$ either. Hence it depends only on the magnitude of the velocity, $\textbf v^{2}= v^2$.

Since the lagrangian $L(v^2)$ doesn't depend on $\textbf r$, [[Lagrange's equations]] take the form
$$\frac{d}{dt} \frac{\partial L}{\partial \textbf v} = 0.$$
This then means that $\partial L/\partial \textbf v= \text{constant}$, as time goes on. But since $\partial L /\partial \textbf v$ is a function of the velocity only (and it must have some explicit dependence on $\textbf v$ since $L$ is not linear in $\textbf v$ so the derivative doesn't eliminate it), this must mean that the velocity itself is constant as time goes on, otherwise $\partial L /\partial \textbf v$ would vary with time. Hence we reach that $\textbf v = \text{constant}$, which is the *law of inertia*.

It is worth noting also that the argument above breaks if we just take $L(v^{2}) = \text{constant}$, in which case the conditions above all apply correctly, but the argument breaks down since we can't say that $\partial L /\partial \textbf v$ is explicitly a function of $\textbf v$. However, we can disregard this case because the lagrangian $L(v^{2})=\text{constant}$ makes no sense physically, as it implies that the state of the system depends on absolutely nothing, and would give meaningless equations of motion, which can only be the case for a system with zero particles.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.5.