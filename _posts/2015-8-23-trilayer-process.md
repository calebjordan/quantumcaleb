---
title: 3-Layer Niobium Process
layout: post
tags: Fabrication
---

<!-- MarkdownTOC -->

1. [Stack](#stack)
2. [Process](#process)

<!-- /MarkdownTOC -->


<a name="stack"></a>
## Stack


SiOx
Niobium

<a name="process"></a>
## Process

1. Ground Layer
    We aim for a 100nm thick Nb ground plane to work as our ground layer.
	1. Deposition
    * Deposit in the sputtering system at SU. See [Sputtering Niobium](/2015/08/23/sputtering-nb.html).

	2. Definition
    * Pattern using positive resist. See [Spinning Wafers](/2015/07/31/Spinning Wafers.html).
        - **ARC** DSK101-312 *185C for 90s*
        - **DUV resist** UV210-06 *135C for 60s* 
    * Expose layer 0 (alignment marks) and layer 1 on the [ASML](/2015/7/31/asml-stepper.html).
    * Etch in the [PT740](/2015/07/31/PT740.html).

2. SiOx Layer
    We want a 120nm layer of SiOx to form the dielectric for capacitors, as well as the support material for grounding straps. 
	1. Deposition
    * Deposit using the [Oxford PECVD system](/2015/08/05/Oxford-PECVD.html).
	2. Definition
    * Pattern using negative resist. See [Spinning Wafers](/2015/07/31/Spinning Wafers.html#silicon-dioxide).
    * Expose layer 2 on the [ASML](/2015/7/31/asml-stepper.html).

3. Top Layer
	1. Deposition
	2. Definition

4. Junction Layer
    1. Definition
    2. Deposition
    3. Lift Off
