202404262115
Status: #idea
Tags: [[Differential geometry]]

# Integration of differential 1-forms

The purpose of differential forms is to integrate them. [[Differential 1-form]]s can be integrated over oriented (has positive and negative directions) closed segments of curves. How?

On a segment $\Gamma$ of a curve in the plane, pick an orienting parameter $u$. That is, we let $\Gamma$ be represented by a smooth mapping $\gamma: I \to \textbf R^2$ from an interval in the $u$-axis to the plane. The integral of the differential 1-form $\omega$ along the curve $\Gamma$ is then defined to be
$$\int_{\Gamma} \omega = \int_I \omega(\gamma \prime) du, \hspace{0.3cm}\text{ where  } \hspace{0.1cm} \gamma \prime = d\gamma/du.$$
In other words, the integral of $\omega$ is the limit of the integral sums $\sum \omega(\textbf A_i)$, where $\textbf A_{i} = \gamma \prime(u_i) \Delta_i$, and $\Delta_i$ is the difference $u_{i+1} - u_i$ (see the figure below). That is, each $\textbf A_i$ is the tangent derivative vector at the point corresponding to $u_i$ on the curve, scaled by $\Delta_i$ so that it's *almost* the same as the chord to the next point on the curve corresponding to $u_{i+1}$. As we take the limit and increase the number of divisions of the $u$-axis, and correspondingly the curve, the $\textbf A_i$ get closer and closer to being the chords connecting adjacent points, and fitting the curve perfectly, and so the sum of their 1-form values approaches the integral of the 1-form over the curve.
![[diff_1-form_integration.png]]


___
# References
[[📕 Ordinary Differential Equations - V.I. Arnold]], pgs. 20, 21.