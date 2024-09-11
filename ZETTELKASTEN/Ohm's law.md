202405101503
Status: #idea
Tags: [[Circuit analysis]]

# Ohm's law

*Ohm's law* is an empirical statement about some materials and their resistance. It is of the form
$$R = V/I,$$
that is, it states that the [[Resistance]] of the (Ohmic) material is the ratio of the applied [[Voltage]] and the [[Current]] that voltage draws.

Materials to which Ohm's law applies are called *Ohmic* materials, and they are those materials whose resistance is constant over a range of voltages, and it's given by the formula above. The figure below shows the constant slope $V$-$I$ relation charactertistic of Ohmic materials. 

Nonohmic materials have resistances that vary with voltages, such as diodes, whose resistance is zero when voltage is positive, and very high when voltage is flipped to negative. Ohm's law does not apply here.

It is also important to note that Ohm's law defines **resistance** in terms of voltage and current, *not* voltage in terms of current and resistance. Do not let the fact that Ohm's law is usually written as $V = IR$ confuse you. Voltage is applied completely independently of the material or its resistance, and the resistance is only then defined by the amount of current that that voltage draws.
Of course, Ohm's law can still be used algebraically to tell you the voltage required to pass a given current through some known resistance, as is done often in circuit analysis, but just take care to understand what it's actually saying.

![[ohmic_materials.png]]

___
# References
[[📕 Practical Electronics for Inventors - Scherz & Monk]], pg.23.