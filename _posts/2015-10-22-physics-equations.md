---
title: Equations
layout: post
tag: Physics
---

<!-- MarkdownTOC depth=0 -->

- [Circuits](#circuits)
	- [Passive Components](#passive-components)
		- [Capacitors](#capacitors)
		- [Inductors](#inductors)
	- [Active Components](#active-components)
		- [Amplifiers](#amplifiers)
		- [Attenuators](#attenuators)
- [Microwave Engineering](#microwave-engineering)
- [Superconductors](#superconductors)
- [Josephson Junctions](#josephson-junctions)
- [Circuit QED](#circuit-qed)
	- [Qubits](#qubits)
		- [Transmons](#transmons)
	- [Superconducting Cavities](#superconducting-cavities)

<!-- /MarkdownTOC -->


<a name="circuits"></a>
## Circuits
<a name="passive-components"></a>
### Passive Components

|           Name          |   Symbol  |         Equation        |           Notes           |
| ----------------------- | --------- | ----------------------- | ------------------------- |
| Johnson Noise (Voltage) | $$ V_R $$ | $$ \sqrt{4k_B T R B} $$ | B - Bandwidth             |
| Johnson Noise (Power)   | $$ P_R $$ | $$ k_B T B $$           | Independent of Resistance |
|                         |           |                         |                           |


<a name="capacitors"></a>
#### Capacitors

|           Name           |  Symbol  |                      Equation                      |
|--------------------------|----------|----------------------------------------------------|
| Parallel Plate Capacitor | \\(C \\) | \\(\frac{\epsilon_0 A }{d}\\)                    |
| Energy in a Capacitor    | \\(E \\) | \\(\frac{Q^2}{2C}=\frac{QV}{2}=\frac{CV^2}{2}\\) |

<a name="inductors"></a>
#### Inductors

|        Name       |   Symbol  |         Equation        |
| ----------------- | --------- | ----------------------- |
| Inductive Voltage | $$ V_I $$ | $$ L \frac{d I}{d t} $$ |
|                   |           |                         |







<a name="active-components"></a>
### Active Components

<a name="amplifiers"></a>
#### Amplifiers

|        Name       |    Symbol   |             Equation             |         Notes          |
| ----------------- | ----------- | -------------------------------- | ---------------------- |
| Noise Temperature | $$ T\_{N}$$ | $$ G (T\_{amp} + T\_{Source}) $$ | G - Gain(linear scale) |
|                   |             |                                  |                        |

<a name="attenuators"></a>
#### Attenuators

|        Name       |    Symbol   |             Equation             |         Notes          |
| ----------------- | ----------- | -------------------------------- | ---------------------- |
| Noise Temperature | $$ T\_{N}$$ | $$ G (T\_{att} + T\_{Source}) $$ | G - Gain(linear scale) |
|                   |             |                                  |                        |







<hr>
<a name="microwave-engineering"></a>
## Microwave Engineering









<hr>
<a name="superconductors"></a>
## Superconductors

| Name | Symbol | Equation |
| ---- | ------ | -------- |
|      |        |          |









<hr>
<a name="josephson-junctions"></a>
## Josephson Junctions

|            Name            |  Symbol |                   Equation                  |  Source |
| -------------------------- | ------- | ------------------------------------------- | ------- |
| Josephson Current Relation | $$I$$   | $$I_0\sin{\gamma}$$                         |         |
| Josephson Voltage Relation | $$V$$   | $$ \frac{\Phi_0}{2\pi}\frac{d\gamma}{dt} $$ |         |
| Josephson Inductance       | $$L_c$$ | $$ \frac{\hbar}{2eI_C}$$                    | [Gross] |
|                            |         |                                             |         |











<hr>
<a name="circuit-qed"></a>
## Circuit QED

|               Name              |       Symbol      |                                              Equation                                             | Source |
| ------------------------------- | ----------------- | ------------------------------------------------------------------------------------------------- | ------ |
| Jaynes-Cummings Hamiltonian     | $$ H_{JC}/\hbar$$ | $$ \omega\_r(a^\dagger a + 1/2) + \frac{\omega\_a}{2}\sigma_z + g(a^\dagger\sigma^- + a\sigma^+) $$ |        |
| Dispersive Limit JC Hamiltonian | $$ H/\hbar$$      | $$(\omega\_r + \frac{g^2}{\Delta}\sigma\_Z)(a^\dagger a + 1/2) + \omega_a\sigma\_Z /2 $$             |        |
|                                 |                   |                                                                                                   |        |

<a name="qubits"></a>
### Qubits
|       Name       |    Symbol   |                       Equation                       | Source |
| ---------------- | ----------- | ---------------------------------------------------- | ------ |
| Hamiltonian      | \\(H \\)    | \\(4E\_C (n-n\_g)^2 - E\_J\cos{\varphi}\\)           |        |
| Josephson Energy | \\(E\_J \\) | \\(E\_{J,max}\cos{\left(\pi\Phi / \Phi\_0\right)}\\) |        |
|                  |             |                                                      |        |



<a name="transmons"></a>
#### Transmons
|      Name     |    Symbol    | Equation | Source |
| ------------- | ------------ | -------- | ------ |
| anharmonicity | $$ \alpha $$ |          |        |

{%cite PhysRevA.76.042319%}

<a name="superconducting-cavities"></a>
### Superconducting Cavities
|      Name      |    Symbol    |                                         Equation                                         |
| -------------- | ------------ | ---------------------------------------------------------------------------------------- |
| Transmission   | $$ S_{21} $$ | $$ \frac{\left&#124;S\_{21}\right&#124;}{\sqrt{1+4Q^2\left(\frac{f\_0}{f}-1\right)^2}}$$ |
| Quality Factor | $$Q$$        | $$ \frac{f\_0}{ \Delta f\_{3dB}}$$                                                       |
| Loss Rate      | $$\kappa$$   | $$\frac{2\pi f\_0}{Q} = 2\pi \Delta f\_{3dB}$$                                           |
|                |              |                                                                                          |

<hr>
{% bibliography --cited %}