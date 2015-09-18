---
layout: post
title: Spinning Wafers
tags: Fabrication
---

<!-- MarkdownTOC -->

1. [Metal Layers](#metal-layers)
    1. [Niobium](#niobium)
    2. [Aluminum](#aluminum)
2. [Dielectric Layers](#dielectric-layers)
    1. [Silicon Dioxide](#silicon-dioxide)
3. [Masks](#masks)

<!-- /MarkdownTOC -->


Two photoresist layers are required to expose on the ASML. 

Our resist storage is in drawer 9, in the back right corner.

<a name="metal-layers"></a>
## Metal Layers

<a name="niobium"></a>
### Niobium

#### Layer 1 - Anti-reflection Coating (ARC)
* DSK101-312

* Program DSK101-Ware on the manual spinners.

* \\(\omega = 5000\\), \\(\alpha=10,000\\), \\(t=60s\\)

* Soft Bake 185&deg;C for 90s

#### Layer 2 - DUV Resist
* UV210-06

* Program DUV_Defeo on the manual spinners. 

* [Data Sheet](http://www.microchem.com/PDFs_Dow/UV210%20Data%20Sheet.pdf)

* \\(\omega=3000\\), \\(\alpha=8000\\), \\(t=60s\\)

* Soft Bake 135&deg;C for 60s

<a name="aluminum"></a>
### Aluminum

<a name="dielectric-layers"></a>
## Dielectric Layers

<a name="silicon-dioxide"></a>
### Silicon Dioxide

#### Layer 1 - Anti-reflection Coating (ARC)
* DSK101-312

* Program DSK101-Ware on the manual spinners.

* \\(\omega = 5000\\), \\(\alpha=10,000\\), \\(t=60s\\)

* Soft Bake 185&deg;C for 90s

#### Layer 2 - Negative DUV Resist
* UVN230
* [Data Sheet](http://www.microchem.com/PDFs_Dow/UVN30%20Datasheet.pdf)
* Soft Bake 110&deg;C for 60s
* PEB 105&deg;C for 60s

<a name="masks"></a>
## Masks

If for some reason you screw up a mask (before etching) and want to save $275 (or can't wait for the CNF guys to sell you a new one), you can respin your own resist and reuse the mask. 

1. Rinse the resist in the strip bath
2. Spin dry
3. Bake for a minute or so on any hotplate over 100C. You want to get all of the water out of the quartz. 
4. Spin on some 1805 resist from the general drawer. Use the large spinner in the e-beam spinner room. You may need to swap out the holder to hold a 5inch mask. Spin at 2000 RPM for a minute. You'll probably need to clean the spinner afterwards, just use an acetone-IPA rinse. 
5. Bake at 115&deg;C for 60s


