202404270044
Status: #idea
Tags: [[Differential equations]]

# Mnemonic rule for solution of autonomous differential equations

A mnemonic rule for remembering the formula for the general solution of [[autonomous differential equation]]s is to write out the equation itself $\dot x = v(x)$ as $\frac{dx}{dt} = v(x)$, and then while treating $dx$ and $dt$ as [[differential 1-form]]s, bring all the $x$'s to the right-hand side, and the $t$'s to the left.

We end up with $dt = dx/v(x)$. This is an equality between two differential forms, and it's saying that when evaluating the tangent vectors to the integral curves, the two forms $dt$ and $dx/v(x)$ give the same values. Therefore, their integrals over a segment of an integral curve are equal. Hence, using the second proposition given at the end of the [[Integration of differential 1-forms]] note (which applies since $t$ and $x$ are 1-dimensional axes and so can both parameterize the integral curve), integrating the forms on each side of this last equation reduces to evaluating the usual definite integrals $\int dt$ and $\int dx/v(x)$, giving us the desired general formula:
$$t-t_{0} = \int^{x}_{x_0} \frac{d\xi}{v(\xi)}.$$

___
# References
[[📕 Ordinary Differential Equations - V.I. Arnold]], pgs. 19-21.