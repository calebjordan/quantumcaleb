---
layout: post
title: Qubits for JPM Experiments
tags: Experiments
---
This was my first round of fabrication, going from chip design to experiment. 

# Design
* One or two cavities
* One or two qubits connected to either cavity
* Variable frequencies for both cavities
* Variable capacitances on both ends of both cavities (Variable Q)
* Variable capacitances from qubit to cavity (Variable Cq)
* Flux tunability for either qubit


## Main Layout
I decided for simplicity's sake to have a symmetric layout, although this may make the chip more susceptible to spurious chip modes. The 5GHz cavity is on the left side, and optional 7GHz cavity is in the same position on the right side. Input and output capacitors are symmetrically placed. The qubits are along the y axis and also symmetric in terms of coupling to each cavity. Moving up to an 8mmx8mm chip size has given us a lot of extra room.


## Flux Bias Line
We want to be able to tune two qubits 


# Fabrication
Fabrication of this device was done at CNF. 

Single Layer Niobium (100nm thick)


## Masks
### JPMQubitv1
My first mask was off-center, so the ASML was unable to shoot the qubits and some of the capacitors. 
### JPMQubitv2
The second mask was nearly perfect, but has the flux trapping of the 5GHz resonator length stuck in the single cavity layout, meaning that's the only frequency that can be used with a single cavity. Wafers v3 and v4 were both shot using this mask. 


## Wafers
### v1 
First wafer ever. Epic disaster. Capacitors were misplaced, cavities were shorted to ground. This should have been noticed at CNF. Got butchered on the dicing saw. Got a single good chip out of it, the 5GHz frequency came out at 4.7GHz. Couldn't find the 7GHz cavity, possibly too high a Q. 


**Data**

### v2 
 Pushed the 5GHz up to 5.4GHz.

**Data**

### v3
 High Ω, 4 quadrants. 

**A**

* Single Cavity, single qubit
* **5GHz** Cin6, Cout2, 5GHz

<img src="http://quantumcaleb.com/content/images/2015/07/A.jpg" width="500">
<img src="http://quantumcaleb.com/content/images/2015/07/1-Zoomedin.png" width="500">

**B**

* Double Cavity, single qubit
* **5GHz** Cin6, Cout3, 5.5GHz
* **7GHz** Cin4, 6.5GHz

<img src="http://quantumcaleb.com/content/images/2015/07/B.jpg" width="500">

**C**

* Double Cavity, double qubit
* **5GHz** Cin6, Cout4, 5GHz
* **7GHz** Cin5, 7GHz

<img src="http://quantumcaleb.com/content/images/2015/07/C.jpg" width="500">

**D**

* Double Cavity, single qubit
* **5GHz** Cin6, Cout5, 5.5GHz
* **7GHz** Cin6, 7GHz

<img src="http://quantumcaleb.com/content/images/2015/07/D.jpg" width="500">
<img src="http://quantumcaleb.com/content/images/2015/07/2-Zoomedout.png" width="500">

Two chips (A, D) successfully extracted, 100% dicing efficiency. Both chips successfully bonded and measured. 

**Data**

### v4 
High Ω.

**A, B**  

* Double Cavity, Double Tunable Qubit, Cq1
* **5GHz** Cin6, Cout5, 5.5GHz
* **7GHz** Cin5, 7GHz

**C**

* **5GHz** Cout4

**D**

* **5GHz** Cout3
   
Every third die was a test junction with E-Beam alignment marks at ±3.5, 0 mm. 

Matt H wrote qubits on this wafer, as we were in a rush and I am not yet trained on the JEOL 9500. 

**Data**

## Evaporating Josephson Junctions

This was my first time developing Josephson Junctions. Parameters/Results are as follows

| Sample | Type | Chamber Pressure | \\(O_2\\) Pressure | Oxidation Time (min) | Resistance | Frequency |
|--------|------|------------------|--------------------|----------------------|------------|-----------|
| qubitjpm1 | One Qubit | 5e-8 | 30 | 30 | xkOhm | 5.5GHz |
| qubitjpm2 | x | x | x | x | x | x |
| qubitjpm3 | x | x | x | x | x | x |
| qubitjpm4 | x | x | x | x | x | x |

## Dicing
This was the first chip to be diced for use with the new 8mm sample boxes, so some iterations were needed to dial in the dicing. I added some crosshair guides on the chip corners to help with lining up on the dicing saw. Next step is to make the chip spacing the width of the dicing blade so that only one pass is needed. 




# Experiments

