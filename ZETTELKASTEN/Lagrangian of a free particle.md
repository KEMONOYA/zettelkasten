202404271908
Status: #idea
Tags: [[Mechanics]]

# Lagrangian of a free particle

The form of the [[Lagrangian]] for the simplest system, a system of one free particle, is $L = \frac{1}{2} mv^2$.

We can derive this form using [[Galileo's relativity principle]]. Start with an inertial frame $K$ moving relative to another inertial frame $K^\prime$ with infinitesimal velocity $\boldsymbol \epsilon$, so that the velocity of the particle in frame $K^\prime$ is related to that of $K$ by $\textbf v^{\prime}= \textbf v + \boldsymbol \epsilon$. 

Since the frames are inertial, we know that the lagrangian of a free particle in frame $K$ is of the form $L(v^2)$, it depends only on the square of the velocity. By Galileo's relativity principle, the equation of motion of the particle is the same in both frames, so the lagrangian $L^\prime$ of the system in frame $K^\prime$ can differ from $L(v^2)$ of $K$ only by the total time derivative of a function of coordinates and time. Transforming the lagrangian of $K$, we get
$$L^{\prime}= L({v^\prime}^{2})=L(v^{2}+2 \textbf v \cdot \boldsymbol \epsilon + \epsilon^2),$$
and expanding the last side in powers of $\epsilon$ (by taking center of expansion to be $v^2$) up to first order terms (higher order terms can be neglected since $\epsu$), we get
$$L({{v^{\prime}}^{2}})=L(v^{2}) + \frac{\partial L}{\partial v^{2}} 2\textbf v \cdot \boldsymbol \epsilon.$$
Now $L^\prime$ can only differ from $L$ by a total time derivative, so the second term on the right must be one. And for that to be so, that term must be a linear function of $\textbf v$ (since the total time derivative of a function $f(\textbf r, t)$ equals $\frac{\partial f}{\partial \textbf r} \frac{\partial \textbf r}{\partial t} + \frac{\partial f}{\partial t} = \frac{\partial f}{\partial \textbf r} \textbf v + \frac{\partial f}{\partial t}$). Therefore, $\partial L / \partial v^2$ must be independent of the velocity, since the linear $\textbf v$ is already included in $2\textbf v \cdot \boldsymbol \epsilon$ so we can't multiply other $\textbf v$'s with it.

This then means that $L$ is proportional to $v^2$, which means it is of the form $L = \frac{1}{2}mv^2$. 

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pgs. 6,7.