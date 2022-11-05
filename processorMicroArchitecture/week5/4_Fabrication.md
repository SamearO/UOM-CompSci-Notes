# Transistor Fabrication

* Transistors are made using litography with 2 main parameters, the `gate width` and `gate length`.
* The `gate length` needs to be minimised.
* The `gate width` determines the drive strength of the transistor (power of the output).

## Capacitive Load

* Every component, including the wires have capacitance.
* The capacitance is dominated by the wires.
* Power dissipation when the CMOS circuit is static is quite low.
* The power dissipation is proportional to the `Capacitance* Voltage^2`

## Power Dissipation during switching

* There is time taken for the switching of transistors between `on` and `off`.
* In the time between `0` and `1`, it is possible that both the `pull up` and `pull down` network are on at the same time hence power is shorted from the power supply to ground.
* This leads to high power dissipation.
* The amount of power dissipated can be reduced by reducing the power supply voltage however, this reduces the amount of difference between a `1` and a `0` which can make circuits unstable.