202404261900
Status: #idea
Tags: [[Differential equations]]

# Autonomous differential equation

A differential equation is called *autonomous* if it has no explicit dependence on its independent variable. The motivation for this concept is closed mechanical systems, systems that don't interact with any other systems and hence are not dependent on time, since the laws of nature do not change with time.

For instance, in the case of [[Newton's equations]], the equation of motion $\ddot x = F(x,\dot x)$ expressing an isolated mechanical system is autonomous since $F$ is independent of $t$.

A first-order autonomous differential equation $\dot x = v(x)$ has a general solution satisfying the initial conditions $(t_0,x_0)$ given by [[Barrow's formula]] (after converting the equation to the equivalent form $\frac{dt}{dx}= 1/v(x)$ exploiting the independence on t, so that the formula applies):
$$t - t_{0}= \int^x_{x_0} \frac{d\xi}{v(\xi)}.$$
See also the [[Mnemonic rule for solution of autonomous differential equations]].

___
# References
[[📕 Ordinary Differential Equations - V.I. Arnold]], pg.19.