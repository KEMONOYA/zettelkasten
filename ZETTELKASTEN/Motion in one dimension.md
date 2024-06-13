202405232150
Status: #idea
Tags: [[Mechanics]]

# Motion in one dimension

A mechanical system is said to move *in one dimension* if it has only one degree of freedom. The [[Lagrangian]] of such a system is in general of the form $L = \frac{1}{2}a(q)\dot q^2-U(q)$ (*note*: $a(q)$ depends on $q$ when we use curved coordinates, since the length of the radius coordinate affects how much a change in the angle coordinate moves the particle; the arc length). In the case of a Cartesian coordinate (say, $x$), the lagrangian becomes
$$L = \frac{1}{2}m\dot x^2-U(x).$$
In this case, the motion of the system is integrable in a general form, without even writing down the equation of motion. We can start from the first integral of the equation, which is the law of conservation of [[energy]], giving us the first-order differential equation
$$\frac{1}{2}m\dot x^2 +U(x)=E.$$
This is a first-order [[autonomous differential equation]], and hence can be solved by rewriting it as
$$\frac{dx}{dt}=\sqrt{\frac{2}{m}(E-U(x))}$$
and using [[Barrow's formula]] to get the solution
$$t=\sqrt{\frac{1}{2}m}\int \frac{dx}{\sqrt{E-U(x)}}+\text{constant.}$$
The two arbitrary constants in this solution are represented by the energy $E$ and the constant of integration.

___
# References
[[📕 Mechanics - Landau & Lifshitz]], pg.25.