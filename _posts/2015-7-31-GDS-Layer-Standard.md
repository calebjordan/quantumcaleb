---
layout: post
title: Layer Standard for GDS Files
tags: Fabrication Software
---
I will try to keep to the following standard when creating GDS files.

## Layer 0

* **0/0** Absolute Size limits


## Layer 1
* **1/0** Features in Ground Layer
* **1/1** Final Ground Layer to be shot. Combine all other layers into this before exporting to mask gds.
* **1/2** Subtraction Layer
* **1/3** Pockets / Bounding Boxes
* **1/4** Flux Trapping. The many 4x4um square holes in the ground plane that trap vortices. 

## Layer 2
* **2/0** Features in Layer 2
* **2/1** Final Layer 2
* **2/2** Subtraction Layer

## Layer 3
* **3/0** Features in Layer 3
* **3/1** Final Layer 3
* **3/2** Subtraction Layer
