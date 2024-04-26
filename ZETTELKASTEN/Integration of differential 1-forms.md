202404262115
Status: #idea
Tags: [[Differential geometry]]

# Integration of differential 1-forms

The purpose of differential forms is to integrate them. [[Differential 1-form]]s can be integrated over oriented (has positive and negative directions) closed segments of curves. How?

On a segment $\Gamma$ of a curve in the plane, pick an orienting parameter $u$. That is, we let $\Gamma$ be represented by a smooth mapping $\gamma: I \to \textbf R^2$ from an interval in the $u$-axis to the plane. The integral of the differential 1-form $\omega$ along the curve $\Gamma$ is then defined to be
$$\int_{\Gamma} \omega = \int_I \omega(\gamma \prime) du, \hspace{0.3cm}\text{ where  } \hspace{0.1cm} \gamma \prime = d\gamma/du.$$
In other words, the integral of $\omega$ is the limit of the integral sums $\sum \omega(\textbf A_i)$, where $\textbf A_{i} = \gamma \prime(u_i) \Delta_i$, and $\Delta_i$ is the difference $u_{i+1} - u_i$ (see the figure below). That is, each $\textbf A_i$ is the derivative vector at the point corresponding to $u_i$, scaled by $\Delta_i$ so that it's *almost* the same as the chord to the point corresponding to $u_{i+1}$.
![[diff_1-form_integration.png]]


___
# References
[[📕 Ordinary Differential Equations - V.I. Arnold]], pgs. 20, 21.